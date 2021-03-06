---
author: alkohli
ms.service: databox
ms.subservice: pod
ms.topic: include
ms.date: 09/git14/2020
ms.author: alkohli
ms.openlocfilehash: 91f91b1260cc445f90c2608fc5259ad61acd37ac
ms.sourcegitcommit: 829d951d5c90442a38012daaf77e86046018e5b9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2020
ms.locfileid: "90533374"
---
아래에는 Data Box 디바이스용으로 지원되는 스토리지 계정 및 스토리지 유형의 목록이 나와 있습니다. 모든 유형의 스토리지 계정과 해당 계정의 모든 기능이 포함된 전체 목록은 [스토리지 계정의 유형](/azure/storage/common/storage-account-overview#types-of-storage-accounts)을 참조하세요.

가져오기 주문의 경우 다음 표에서는 지원 되는 저장소 계정을 보여 줍니다.

| **스토리지 계정/지원되는 스토리지 유형** | **블록 Blob** |**페이지 Blob*** |**Azure 파일** |**참고 사항**|
| --- | --- | -- | -- | -- |
| Classic Standard | Y | Y | Y |
| 범용 v1 Standard  | Y | Y | Y | 핫 및 쿨이 모두 지원됩니다.|
| 범용 v1 Premium  |  | Y| | |
| 범용 v2 Standard  | Y | Y | Y | 핫 및 쿨이 모두 지원됩니다.|
| 범용 v2 Premium  |  |Y | | |
| Blob Storage Standard |Y | | |핫 및 쿨이 모두 지원됩니다. |

\*  *- 페이지 Blob에 업로드된 데이터는 VHD와 같이 512바이트로 정렬되어야 합니다.*

내보내기 주문의 경우 다음 표에서는 지원 되는 저장소 계정을 보여 줍니다.

| **스토리지 계정/지원되는 스토리지 유형** | **블록 Blob** |**페이지 Blob*** |**Azure 파일** |**지원되는 액세스 계층**|
| --- | --- | -- | -- | -- |
| Classic Standard | Y | Y | Y | |
| 범용 v1 Standard  | Y | Y | Y | 핫, 쿨|
| 범용 v1 Premium  |  | Y| | |
| 범용 v2 Standard  | Y | Y | Y | 핫, 쿨|
| 범용 v2 Premium  |  |Y | | |
| Blob Storage Standard |Y | | |핫, 쿨 |
| 블록 Blob storage Premium |Y | | |핫, 쿨 |
| 페이지 Blob storage Premium | |Y | | |

> [!IMPORTANT]
> - 범용 계정의 경우에는 Data Box에서 가져오기 순서에 대 한 큐, 테이블 및 디스크 저장소 형식을 지원 하지 않습니다. 내보내기 주문의 경우 Data Box는 범용 계정에 대 한 Queue, Table, Disk 및 Azure Data Lake Gen 2 저장소 형식을 지원 하지 않습니다.
> - Data Box는 Blob Storage 및 블록 Blob Storage 계정에 대 한 추가 blob을 지원 하지 않습니다.
> - Data Box는 Premium File Storage 계정을 지원 하지 않습니다.
> - 페이지 blob에 업로드 된 데이터는 Vhd와 같이 512 바이트 정렬 되어야 합니다.
> - 최대 80 TB를 내보낼 수 있습니다.
> - 파일 기록과 blob 스냅숏은 내보내지 않습니다.


