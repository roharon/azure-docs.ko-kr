---
title: Azure CLI를 사용하여 공용 IP 주소에 대한 라우팅 기본 설정 구성
titlesuffix: Azure Virtual Network
description: Azure CLI를 사용 하 여 인터넷 트래픽 라우팅 기본 설정으로 공용 IP를 만드는 방법에 대해 알아봅니다.
services: virtual-network
documentationcenter: na
author: KumudD
manager: mtillman
ms.service: virtual-network
ms.devlang: na
ms.topic: how-to
ms.tgt_pltfrm: na
ms.workload: infrastructure-services
ms.date: 05/18/2020
ms.author: mnayak
ms.custom: devx-track-azurecli
ms.openlocfilehash: 5e7a8c5552165324ef154767d1605e12b0c9ad22
ms.sourcegitcommit: c2dd51aeaec24cd18f2e4e77d268de5bcc89e4a7
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94747862"
---
# <a name="configure-routing-preference-for-a-public-ip-address-using-azure-cli"></a>Azure CLI를 사용하여 공용 IP 주소에 대한 라우팅 기본 설정 구성

이 문서에서는 Azure CLI를 사용하여 공용 IP 주소에 대해 ISP 네트워크(**인터넷** 옵션)를 통해 라우팅 기본 설정을 구성하는 방법을 보여줍니다. 공용 IP 주소를 만든 후 인터넷에 대한 인바운드 및 아웃바운드 트래픽을 위해 다음 Azure 리소스와 연결할 수 있습니다.

* 가상 머신
* 가상 머신 크기 집합
* AKS(Azure Kubernetes Service)
* 인터넷 연결 부하 분산 장치
* Application Gateway
* Azure Firewall

기본적으로 공용 IP 주소에 대한 라우팅 기본 설정은 모든 Azure 서비스에 대해 Microsoft 글로벌 네트워크로 설정되며 모든 Azure 서비스에 연결할 수 있습니다.

> [!IMPORTANT]
> 라우팅 기본 설정은 현재 공개 미리 보기로 제공됩니다.
> 이 미리 보기 버전은 서비스 수준 계약 없이 제공되며 프로덕션 워크로드에는 사용하지 않는 것이 좋습니다. 특정 기능이 지원되지 않거나 기능이 제한될 수 있습니다. 자세한 내용은 [Microsoft Azure Preview에 대한 추가 사용 약관](https://azure.microsoft.com/support/legal/preview-supplemental-terms/)을 참조하세요.

[!INCLUDE [quickstarts-free-trial-note](../../includes/quickstarts-free-trial-note.md)]

[!INCLUDE [azure-cli-prepare-your-environment.md](../../includes/azure-cli-prepare-your-environment.md)]

- 이 문서에는 Azure CLI 버전 2.0.49 이상이 필요 합니다. Azure Cloud Shell을 사용하는 경우 최신 버전이 이미 설치되어 있습니다.

## <a name="register-the-feature-for-your-subscription"></a>구독에 대한 기능 등록
라우팅 기본 설정 기능은 현재 미리 보기로 제공됩니다. 다음과 같이 구독에 대한 기능을 등록합니다.
```azurecli
az feature register --namespace Microsoft.Network --name AllowRoutingPreferenceFeature
```

## <a name="create-a-resource-group"></a>리소스 그룹 만들기
[az group create](/cli/azure/group#az-group-create) 명령을 사용하여 리소스 그룹을 만듭니다. 다음 예제에서는 **미국 동부** Azure 지역의 리소스 그룹을 만듭니다.

```azurecli
  az group create --name myResourceGroup --location eastus
```
## <a name="create-a-public-ip-address"></a>공용 IP 주소 만들기

아래에 같은 형식으로 [az network public-ip create](/cli/azure/network/public-ip?view=azure-cli-latest#az-network-public-ip-create) 명령을 사용하여 "인터넷" 유형의 라우팅 기본 설정으로 공용 IP 주소를 만듭니다.

다음 명령은 **미국 동부** Azure 지역에서 **인터넷** 라우팅 기본 설정으로 새 공용 IP를 만듭니다.

```azurecli
az network public-ip create \
--name MyRoutingPrefIP \
--resource-group MyResourceGroup \
--location eastus \
--ip-tags 'RoutingPreference=Internet' \
--sku STANDARD \
--allocation-method static \
--version IPv4
```

> [!NOTE]
>  현재 라우팅 기본 설정은 IPV4 공용 IP 주소만 지원합니다.

위에서 만든 공용 IP 주소를 [Windows](../virtual-machines/windows/overview.md?toc=%2fazure%2fvirtual-network%2ftoc.json) 또는 [Linux](../virtual-machines/linux/overview.md?toc=%2fazure%2fvirtual-network%2ftoc.json) 가상 머신과 연결할 수 있습니다. 자습서 페이지의 CLI 섹션을 사용합니다. [공용 IP 주소를 가상 머신에 연결](associate-public-ip-address-vm.md#azure-cli)하여 공용 IP를 VM에 연결합니다. 위에서 만든 공용 IP 주소를 부하 분산 장치 **프런트 엔드** 구성에 할당하여 [Azure Load Balancer](../load-balancer/load-balancer-overview.md)와 연결할 수도 있습니다. 공용 IP 주소는 부하가 분산된 VIP(가상 IP 주소)로 사용됩니다.

## <a name="next-steps"></a>다음 단계

- [공용 IP 주소의 라우팅 기본 설정](routing-preference-overview.md)에 대해 자세히 알아봅니다. 
- [Azure CLI를 사용하여 VM에 대한 라우팅 기본 설정을 구성합니다](configure-routing-preference-virtual-machine-cli.md).

