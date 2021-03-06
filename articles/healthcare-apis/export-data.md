---
title: FHIR 용 Azure API에서 $export 명령을 호출 하 여 내보내기 실행
description: 이 문서에서는 $export를 사용 하 여 FHIR 데이터를 내보내는 방법을 설명 합니다.
author: matjazl
ms.service: healthcare-apis
ms.subservice: fhir
ms.topic: reference
ms.date: 8/26/2020
ms.author: matjazl
ms.openlocfilehash: 74fe09895f49cc9f7c3cdf6b6c97c1624c3e9c0b
ms.sourcegitcommit: 829d951d5c90442a38012daaf77e86046018e5b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91839829"
---
# <a name="how-to-export-fhir-data"></a>FHIR 데이터를 내보내는 방법


대량 내보내기 기능을 사용 하면 [fhir 사양](https://hl7.org/fhir/uv/bulkdata/export/index.html)에 따라 Fhir 서버에서 데이터를 내보낼 수 있습니다. 

$Export를 사용 하기 전에 FHIR 용 Azure API가이를 사용 하도록 구성 되어 있는지 확인 해야 합니다. 내보내기 설정 구성 및 Azure storage 계정 만들기 [는 데이터 내보내기 구성 페이지](configure-export-data.md)를 참조 하세요.

## <a name="using-export-command"></a>$export 명령 사용

내보내기에 대 한 Azure API를 구성 하 고 나면 $export 명령을 사용 하 여 서비스에서 데이터를 내보낼 수 있습니다. 데이터는 내보내기를 구성 하는 동안 지정한 저장소 계정에 저장 됩니다. FHIR 서버에서 $export 명령을 호출 하는 방법을 알아보려면 [$export 사양](https://hl7.org/Fhir/uv/bulkdata/export/index.html)에 대 한 설명서를 참조 하세요. 

FHIR 용 Azure API의 $export 명령은 구성 된 저장소 계정 내에서 데이터를 내보내야 하는 컨테이너를 지정 하는 선택적 _ \_ 컨테이너_ 매개 변수를 사용 합니다. 컨테이너를 지정 하면 이름이 인 새 폴더의 해당 컨테이너로 데이터가 내보내집니다. 컨테이너를 지정 하지 않으면 임의로 생성 된 이름을 사용 하 여 새 컨테이너로 내보냅니다. 

`https://<<FHIR service base URL>>/$export?_container=<<container_name>>`

## <a name="supported-scenarios"></a>지원되는 시나리오

FHIR 용 Azure API는 시스템, 환자 및 그룹 수준에서 $export을 지원 합니다. 그룹 내보내기의 경우 관련 된 모든 리소스를 내보내고 그룹의 특성은 내보내지 않습니다.

> [!Note] 
> 리소스가 둘 이상의 리소스 구획에 있거나 여러 그룹에 있는 경우에는 중복 리소스를 내보냅니다 $export 합니다.

또한 큐 중에 위치 헤더에서 반환 된 URL을 통해 내보내기 상태를 확인 하는 작업은 실제 내보내기 작업을 취소 하는 것과 함께 지원 됩니다.

## <a name="next-steps"></a>다음 단계

이 문서에서는 $export 명령을 사용 하 여 FHIR 리소스를 내보내는 방법을 배웠습니다. 다음으로 지원 되는 기능을 검토할 수 있습니다.
 
>[!div class="nextstepaction"]
>[지원되는 기능](fhir-features-supported.md)
