---
title: Azure Service Fabric에서 지원 되는 클러스터 버전
description: Service Fabric 팀 블로그의 최신 릴리스에 대 한 링크를 포함 하 여 Azure Service Fabric의 클러스터 버전에 대해 알아봅니다.
ms.topic: troubleshooting
ms.date: 06/15/2020
ms.openlocfilehash: d6469ada7fcb46c732cc7fbe081059ef41d89a40
ms.sourcegitcommit: 9826fb9575dcc1d49f16dd8c7794c7b471bd3109
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/14/2020
ms.locfileid: "94626778"
---
# <a name="supported-service-fabric-versions"></a>지원되는 Service Fabric 버전

클러스터가 항상 지원 되는 Azure Service Fabric 버전을 실행 하 고 있는지 확인 합니다. Service Fabric 새 버전의 릴리스를 발표 한 후 최소 60 일이 지나면 이전 버전에 대 한 지원이 종료 됩니다. [Service Fabric 팀 블로그에서](https://azure.microsoft.com/updates/?product=service-fabric)새 릴리스에 대 한 공지를 확인할 수 있습니다.

지정 된 버전의 Service Fabric 런타임에 대해 지정 된 또는 이전 버전의 SDK/NuGet 패키지를 사용할 수 있습니다. 최신 버전의 패키지가 지원 되지 않으며, 해당 환경에서 지원 하지 않는 기능 또는 프로토콜 변경이 있을 수 있으므로 이전 클러스터를 대상으로 하는 문제가 발생할 수 있습니다.

클러스터에서 지원 되는 Service Fabric 버전을 계속 실행 하는 방법에 대 한 자세한 내용은 다음 문서를 참조 하세요.

- [Azure Service Fabric 클러스터 업그레이드](service-fabric-cluster-upgrade.md)
- [독립 실행형 Windows Server 클러스터에서 실행 되는 Service Fabric 버전을 업그레이드 합니다.](service-fabric-cluster-upgrade-windows-server.md)

## <a name="supported-versions"></a>지원되는 버전

다음 표에서는 Service Fabric 버전 및 지원 종료 날짜를 나열 합니다.

| 클러스터의 Service Fabric 런타임 | 클러스터 버전에서 직접 업그레이드할 수 있습니다. |호환 되는 SDK 또는 NuGet 패키지 버전 | 지원 종료 |
| --- | --- |--- | --- |
| 5.3.121 전 모든 클러스터 버전 | 5.1.158.* |버전 2.3보다 작거나 같음 |2017년 1월 20일 |
| 5.3.* | 5.1.158.* |버전 2.3보다 작거나 같음 |2017년 2월 24일 |
| 5.4.* | 5.1.158.* |버전 2.4보다 작거나 같음 |2017년 5월 10일       |
| 5.5.* | 5.4.164.* |버전 2.5보다 작거나 같음 |2017년 8월 10일    |
| 5.6.* | 5.4.164.* |버전 2.6보다 작거나 같음 |2017년 10월 13일   |
| 5.7.* | 5.4.164.* |버전 2.7보다 작거나 같음 |2017년 12월 15일  |
| 6.0.* | 5.6.205.* |버전 2.8보다 작거나 같음 |2018 년 3 월 30 일     |
| 6.1.* | 5.7.221.* |버전 3.0보다 작거나 같음 |2018 년 7 월 15 일      |
| 6.2.* | 6.0.232.* |버전 3.1보다 작거나 같음 |2018 년 10 월 26 일   |
| 6.3.* | 6.1.480.* |버전 3.2보다 작거나 같음 |2019 년 3 월 31 일  |
| 6.4.* | 6.2.301.* |버전 3.3보다 작거나 같음 |2019 년 9 월 15 일 |
| 6.5. * | 6.4.617.* |버전 3.4 보다 작거나 같음 |2020 년 8 월 1 일 |
| 7.0.466.* | 6.4.664.* |버전 4.0 보다 작거나 같음|2021 년 1 월 31 일  |
| 7.0.466.* | 6.5. * |버전 4.0 보다 작거나 같음|2021 년 1 월 31 일 |
| 7.0.470.* | 7.0.466.* |버전 4.0 보다 작거나 같음 |2021 년 1 월 31 일  |
| 7.0.472.* | 7.0.466.* |버전 4.0 보다 작거나 같음 |2021 년 1 월 31 일  |
| 7.0.478.* | 7.0.466.* |버전 4.0 보다 작거나 같음 |2021 년 1 월 31 일  |
| 7.1.409.* | 7.0.466.* |버전 4.1 보다 작거나 같음 |2021 년 3 월 31 일 |
| 7.1.417.* | 7.0.466.* |버전 4.1 보다 작거나 같음 |2021 년 3 월 31 일 |
| 7.1.428.* | 7.0.466.* |버전 4.1 보다 작거나 같음 |2021 년 3 월 31 일 |
| 7.1.456.* | 7.0.466.* |버전 4.1 보다 작거나 같음 |2021 년 3 월 31 일 |
| 7.1.458.* | 7.0.466.* |버전 4.1 보다 작거나 같음 |2021 년 3 월 31 일 |
| 7.1.459.* | 7.0.466.* |버전 4.1 보다 작거나 같음 |2021 년 3 월 31 일 |
| 7.1.503.* | 7.0.466.* |버전 4.1 보다 작거나 같음 |2021 년 3 월 31 일 |
| 7.2.413.* | 7.0.470.* |버전 4.2 보다 작거나 같음 |현재 버전 이므로 종료 날짜 없음 |
| 7.2.432.* | 7.0.470.* |버전 4.2 보다 작거나 같음 |현재 버전 이므로 종료 날짜 없음 |
| 7.2.433.* | 7.0.470.* |버전 4.2 보다 작거나 같음 |현재 버전 이므로 종료 날짜 없음 |

## <a name="supported-operating-systems"></a>지원되는 운영 체제

다음 표에는 지원 되는 Service Fabric 버전에 대해 지원 되는 운영 체제가 나와 있습니다.

| 운영 체제 | 가장 이른 지원 Service Fabric 버전 |
| --- | --- |
| Windows Server 2012 R2 | 모든 버전 |
| Windows Server 2016 | 모든 버전 |
| Windows Server 1709 | 6.0 |
| Windows Server 1803 | 6.4 |
| Windows Server 1809 | 6.4.654.9590 |
| Windows Server 2019 | 6.4.654.9590 |
| Linux Ubuntu 16.04 | 6.0 |
| Linux Ubuntu 18.04 | 7.1 |

## <a name="supported-version-names"></a>지원 되는 버전 이름

다음 표에는 Service Fabric 버전 이름과 해당 버전 번호가 나와 있습니다.

| 버전 이름 | Windows 버전 번호 | Linux 버전 번호 |
| --- | --- | --- |
| 5.3 RTO | 5.3.121.9494 | 해당 없음 |
| 5.3 CU1 | 5.3.204.9494 | 해당 없음 |
| 5.3 CU2 | 5.3.301.9590 | 해당 없음 |
| 5.3 CU3 | 5.3.311.9590 | 해당 없음 |
| 5.4 CU2 | 5.4.164.9494 | 해당 없음 |
| 5.5 CU1 | 5.5.216.0    | 해당 없음 |
| 5.5 CU2 | 5.5.219.0    | 해당 없음 |
| 5.5 CU3 | 5.5.227.0    | 해당 없음 |
| 5.5 CU4 | 5.5.232.0    | 해당 없음 |
| 5.6 RTO | 5.6.204.9494 | 해당 없음 |
| 5.6 CU2 | 5.6.210.9494 | 해당 없음 |
| 5.6 CU3 | 5.6.220.9494 | 해당 없음 |
| 5.7 RTO | 5.7.198.9494 | 해당 없음 |
| 5.7 CU4 | 5.7.221.9494 | 해당 없음 |
| 6.0 RTO | 6.0.211.9494 | 6.0.120.1 |
| 6.0 CU1 | 6.0.219.9494 | 6.0.127.1 |
| 6.0 CU2 | 6.0.232.9494 | 6.0.133.1 |
| 6.1 CU1 | 6.1.456.9494 | 6.1.183.1 |
| 6.1 CU2 | 6.1.467.9494 | 6.1.185.1 |
| 6.1 CU3 | 6.1.472.9494 | 해당 없음 |
| 6.1 CU4 | 6.1.480.9494 | 6.1.187.1 |
| 6.2 RTO | 6.2.269.9494 | 6.2.184.1 | 
| 6.2 CU1 | 6.2.274.9494 | 6.2.191.1 |
| 6.2 CU2 | 6.2.283.9494 | 6.2.194.1 |
| 6.2 CU3 | 6.2.301.9494 | 6.2.199.1 |
| 6.3 RTO | 6.3.162.9494 | 6.3.119.1 |
| 6.3 CU1 | 6.3.176.9494 | 6.3.124.1 |
| 6.3 CU1 | 6.3.187.9494 | 6.3.129.1 |
| 6.4 RTO | 6.4.617.9590 | 6.4.625.1 |
| 6.4 CU2 | 6.4.622.9590 | 해당 없음 |
| 6.4 CU3 | 6.4.637.9590 | 6.4.634.1 |
| 6.4 CU4 | 6.4.644.9590 | 6.4.639.1 |
| 6.4 CU5 | 6.4.654.9590 | 6.4.649.1 |
| 6.4 CU6 | 6.4.658.9590 | 해당 없음 |
| 6.4 CU7 | 6.4.664.9590 | 6.4.661.1 |
| 6.4 CU8 | 6.4.670.9590 | 해당 없음 |
| 6.5 RTO | 6.5.639.9590 | 6.5.435.1 |
| 6.5 CU1 | 6.5.641.9590 | 6.5.454.1 |
| 6.5 CU2 | 6.5.658.9590 | 6.5.460.1 |
| 6.5 CU3 | 6.5.664.9590 | 6.5.466.1 |
| 6.5 CU5 | 6.5.676.9590 | 6.5.467.1 |
| 7.0 RTO | 7.0.457.9590 | 7.0.457.1 |
| 7.0 CU2 | 7.0.464.9590 | 7.0.464.1 |
| 7.0 CU3 | 7.0.466.9590 | 7.0.465.1 |
| 7.0 CU4 | 7.0.470.9590 | 7.0.469.1 |
| 7.0 CU6 | 7.0.472.9590 | 7.0.471.1 |
| 7.0 CU9 | 7.0.478.9590 | 7.0.472.1 |
| 7.1 RTO | 7.1.409.9590 | 7.1.410.1 |
| 7.1 CU1 | 7.1.417.9590 | 7.1.418.1 |
| 7.1 CU2 | 7.1.428.9590 | 7.1.428.1 |
| 7.1 CU3 | 7.1.456.9590 | 7.1.452.1 |
| 7.1 CU5 | 7.1.458.9590 | 7.1.454.1 |
| 7.1 CU6 | 7.1.459.9590 | 7.1.455.1 |
| 7.1 CU8 | 7.1.503.9590 | 해당 없음 |
| 7.2 RTO | 7.2.413.9590 | 해당 없음 |
| 7.2 CU2 | 7.2.432.9590 | 7.2.431.1 |
| 7.2 CU3 | 7.2.433.9590 | 해당 없음 |

