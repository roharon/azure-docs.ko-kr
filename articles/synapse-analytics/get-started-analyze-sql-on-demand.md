---
title: '자습서: 서버리스 SQL 풀을 사용하여 데이터 분석 시작'
description: 이 자습서에서는 Spark 데이터베이스에 있는 데이터를 사용하여 서버리스 SQL 풀로 데이터를 분석하는 방법을 알아봅니다.
services: synapse-analytics
author: saveenr
ms.author: saveenr
manager: julieMSFT
ms.reviewer: jrasnick
ms.service: synapse-analytics
ms.subservice: sql
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: 4ca9ababbeb7843f1a014a4bd51a5e24a74acbae
ms.sourcegitcommit: 96918333d87f4029d4d6af7ac44635c833abb3da
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93322933"
---
# <a name="analyze-data-with-serverless-sql-pool-in-azure-synapse-analytics"></a>Azure Synapse Analytics에서 서버리스 SQL 풀을 사용하여 데이터 분석

이 자습서에서는 Spark 데이터베이스에 있는 데이터를 사용하여 서버리스 SQL 풀로 데이터를 분석하는 방법을 알아봅니다. 

## <a name="analyze-nyc-taxi-data-in-blob-storage-using-serverless-sql-pool"></a>서버리스 SQL 풀을 사용하여 Blob 스토리지에서 NYC Taxi 데이터 분석

1. **연결됨** 아래의 **데이터** 허브에서 **Azure Blob Storage > 샘플 데이터 세트 > nyc_tlc_yellow** 를 마우스 오른쪽 단추로 클릭하고 **상위 100개 행 선택** 을 선택합니다.
1. 그러면 다음 코드에서 새 SQL 스크립트가 생성됩니다.

    ```
    SELECT
        TOP 100 *
    FROM
        OPENROWSET(
            BULK     'https://azureopendatastorage.blob.core.windows.net/nyctlc/yellow/puYear=*/puMonth=*/*.parquet',
            FORMAT = 'parquet'
        ) AS [result];
    ```
1. **실행** 을 클릭합니다.

## <a name="analyze-nyc-taxi-data-in-spark-databases-using-serverless-sql-pool"></a>서버리스 SQL 풀을 사용하여 Spark 데이터베이스에서 NYC Taxi 데이터 분석

Spark 데이터베이스의 테이블은 자동으로 표시되며, 서버리스 SQL 풀에서 이를 쿼리할 수 있습니다.

1. Synapse Studio에서 **개발** 허브로 이동하여 새 SQL 스크립트를 만듭니다.
1. **연결 대상** 을 **서버리스 SQL 풀** 로 설정합니다.
1. 다음 텍스트를 스크립트에 붙여넣고, 해당 스크립트를 실행합니다.

    ```sql
    SELECT *
    FROM nyctaxi.dbo.passengercountstats
    ```

    > [!NOTE]
    > 서버리스 SQL 풀을 사용하는 쿼리를 처음 실행하는 경우 서버리스 SQL 풀에서 쿼리를 실행하는 데 필요한 SQL 리소스를 수집하는 데 약 10초 정도 걸립니다. 이후 쿼리는 훨씬 더 빠릅니다.
  


## <a name="next-steps"></a>다음 단계

> [!div class="nextstepaction"]
> [스토리지 데이터 분석](get-started-analyze-storage.md)
