---
title: Azure Functions의 네트워킹에 대 한 질문과 대답
description: Azure Functions에서 네트워킹에 대 한 가장 일반적인 질문과 시나리오에 대 한 답변입니다.
ms.topic: troubleshooting
ms.date: 4/11/2019
ms.reviewer: glenga
ms.openlocfilehash: 3e8a992aac95b6c2688cb45aa980bf0b01883a53
ms.sourcegitcommit: 1d6ec4b6f60b7d9759269ce55b00c5ac5fb57d32
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2020
ms.locfileid: "94578232"
---
# <a name="frequently-asked-questions-about-networking-in-azure-functions"></a>Azure Functions의 네트워킹에 대 한 질문과 대답

이 문서에서는 Azure Functions의 네트워킹에 대 한 질문과 대답을 나열 합니다. 보다 포괄적인 개요는 [함수 네트워킹 옵션](functions-networking-options.md)을 참조 하세요.

## <a name="how-do-i-set-a-static-ip-in-functions"></a>함수에서 고정 IP를 설정 어떻게 할까요??

함수를 App Service Environment에 배포 하는 것은 현재 함수에 고정 인바운드 및 아웃 바운드 IP를 사용할 수 있는 유일한 방법입니다. App Service Environment 사용에 대 한 자세한 내용은 App Service Environment를 사용 하 [여 내부 부하 분산 장치 만들기 및 사용](../app-service/environment/create-ilb-ase.md)문서로 시작 합니다.

## <a name="how-do-i-restrict-internet-access-to-my-function"></a>내 함수에 대 한 인터넷 액세스를 제한 어떻게 할까요??

다음과 같은 몇 가지 방법으로 인터넷 액세스를 제한할 수 있습니다.

* [Ip 제한](../app-service/app-service-ip-restrictions.md): ip 범위에 따라 함수 앱에 대 한 인바운드 트래픽을 제한 합니다.
    * IP 제한에서 [서비스 끝점](../virtual-network/virtual-network-service-endpoints-overview.md)을 구성할 수도 있습니다 .이는 특정 가상 네트워크에서 인바운드 트래픽만 허용 하도록 함수를 제한 하는 것입니다.
* 모든 HTTP 트리거를 제거 합니다. 일부 응용 프로그램의 경우 단순히 HTTP 트리거를 방지 하 고 다른 이벤트 소스를 사용 하 여 함수를 트리거하는 것 만으로도 충분 합니다.

Azure Portal 편집기는 실행 중인 함수에 직접 액세스 해야 한다는 점에 유의 하세요. Azure Portal를 통해 코드를 변경 하는 경우 포털을 검색 하는 데 사용 하는 장치가 승인 된 목록에 해당 IP를 추가 하도록 요구 합니다. 그러나 여전히 네트워크 제한이 적용 된 플랫폼 기능 탭에서 모든 항목을 사용할 수 있습니다.

## <a name="how-do-i-restrict-my-function-app-to-a-virtual-network"></a>내 함수 앱을 가상 네트워크로 제한 어떻게 할까요??

[서비스 끝점](./functions-networking-options.md#use-service-endpoints)을 사용 하 여 함수 앱에 대 한 **인바운드** 트래픽을 가상 네트워크로 제한할 수 있습니다. 이 구성을 통해 함수 앱에서 인터넷에 대 한 아웃 바운드 호출을 수행할 수 있습니다.

모든 트래픽이 가상 네트워크를 통해 전달 되도록 함수를 완전히 제한 하기 위해 아웃 바운드 가상 네트워크 통합 또는 App Service Environment와 함께 [개인 끝점](./functions-networking-options.md#private-endpoint-connections) 을 사용할 수 있습니다.

## <a name="how-can-i-access-resources-in-a-virtual-network-from-a-function-app"></a>함수 앱에서 가상 네트워크의 리소스에 액세스 하려면 어떻게 해야 하나요?

가상 네트워크 통합을 사용 하 여 실행 중인 함수에서 가상 네트워크의 리소스에 액세스할 수 있습니다. 자세한 내용은 [가상 네트워크 통합](functions-networking-options.md#virtual-network-integration)을 참조 하세요.

## <a name="how-do-i-access-resources-protected-by-service-endpoints"></a>서비스 끝점에 의해 보호 되는 리소스에 액세스 어떻게 할까요??

가상 네트워크 통합을 사용 하면 실행 중인 함수에서 서비스 끝점 보안 리소스에 액세스할 수 있습니다. 자세한 내용은 [가상 네트워크 통합](functions-networking-options.md#virtual-network-integration)을 참조 하세요.

## <a name="how-can-i-trigger-a-function-from-a-resource-in-a-virtual-network"></a>가상 네트워크의 리소스에서 함수를 트리거하는 방법

[서비스 끝점이](./functions-networking-options.md#use-service-endpoints) 나 [개인 끝점 연결](./functions-networking-options.md#private-endpoint-connections)을 사용 하 여 가상 네트워크에서 HTTP 트리거를 호출 하도록 허용할 수 있습니다. 

함수 앱을 프리미엄 계획, App Service 계획 또는 App Service Environment에 배포 하 여 가상 네트워크의 다른 모든 리소스에서 함수를 트리거할 수도 있습니다. 자세한 내용은 [비 HTTP 가상 네트워크 트리거](./functions-networking-options.md#virtual-network-triggers-non-http) 를 참조 하세요.

## <a name="how-can-i-deploy-my-function-app-in-a-virtual-network"></a>가상 네트워크에서 함수 앱을 배포 하려면 어떻게 해야 하나요?

가상 네트워크 내에 있는 함수 앱을 만드는 유일한 방법은 App Service Environment에 배포 하는 것입니다. App Service Environment에서 내부 부하 분산 장치를 사용 하는 방법에 대 한 자세한 내용은 [App Service Environment를 사용 하 여 내부 부하 분산 장치 만들기 및 사용](../app-service/environment/create-ilb-ase.md)문서부터 시작 합니다.

가상 네트워크 리소스에 대 한 단방향 액세스 또는 더 낮은 포괄적인 네트워크 격리를 필요로 하는 시나리오의 경우 [네트워킹 개요 기능](functions-networking-options.md)을 참조 하세요.

## <a name="next-steps"></a>다음 단계

네트워킹 및 기능에 대 한 자세한 내용은 다음을 확인 하세요. 

* [가상 네트워크 통합 시작하기에 관한 자습서 따라하기](./functions-create-vnet.md)
* [에서 네트워킹 옵션에 대해 자세히 알아보세요 Azure Functions](./functions-networking-options.md)
* [App Service 및 함수와의 가상 네트워크 통합에 대해 자세히 알아보기](../app-service/web-sites-integrate-with-vnet.md)
* [Azure의 가상 네트워크에 대해 자세히 알아보기](../virtual-network/virtual-networks-overview.md)
* [App Service Environment로 제어 및 네트워킹 기능 활성화](../app-service/environment/intro.md)
