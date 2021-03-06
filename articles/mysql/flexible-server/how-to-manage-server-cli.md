---
title: 서버 Azure CLI 관리 Azure Database for MySQL 유연한 서버
description: Azure CLI에서 Azure Database for MySQL 유연한 서버를 관리 하는 방법에 대해 알아봅니다.
author: mksuni
ms.author: sumuth
ms.service: mysql
ms.topic: how-to
ms.date: 9/21/2020
ms.openlocfilehash: b58a9dd7901f85c59b09bc4ccb197d012bce2200
ms.sourcegitcommit: d767156543e16e816fc8a0c3777f033d649ffd3c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/26/2020
ms.locfileid: "92545058"
---
# <a name="manage-an-azure-database-for-mysql---flexible-server-preview-using-the-azure-cli"></a>Azure CLI를 사용 하 여 Azure Database for MySQL 유연한 서버 (미리 보기) 관리

> [!IMPORTANT]
> Azure Database for MySQL - 유연한 서버는 현재 공개 미리 보기로 제공됩니다.

이 문서에서는 Azure에 배포 된 유연한 서버 (미리 보기)를 관리 하는 방법을 보여 줍니다. 관리 작업에는 계산 및 저장소 크기 조정, 관리자 암호 재설정 및 서버 세부 정보 보기가 포함 됩니다.

## <a name="prerequisites"></a>사전 요구 사항
Azure 구독이 아직 없는 경우 시작하기 전에 [체험](https://azure.microsoft.com/free/) 계정을 만듭니다. 이 문서에서는 Azure CLI 버전 2.0 이상을 로컬로 실행해야 합니다. 설치된 버전을 확인하려면 `az --version` 명령을 실행합니다. 설치 또는 업그레이드해야 하는 경우 [Azure CLI 설치](/cli/azure/install-azure-cli)를 참조하세요.

[az login](/cli/azure/reference-index#az-login) 명령을 사용하여 계정에 로그인해야 합니다. Azure 계정에 대한 **구독 ID** 를 참조하는 **id** 속성을 기록해 둡니다.

```azurecli-interactive
az login
```

[az account set](/cli/azure/account) 명령을 사용하여 계정에 속한 특정 구독을 선택합니다. 명령에서 **subscription** 인수에 대한 값으로 사용할 **az login** 출력의 **id** 값을 적어 둡니다. 구독이 여러 개인 경우 리소스가 과금되어야 할 적절한 구독을 선택합니다. 모든 구독을 가져오려면 [az account list](/cli/azure/account#az-account-list)를 사용합니다.

```azurecli
az account set --subscription <subscription id>
```

> [!Important]
> 아직 유연한 서버를 만들지 않은 경우이 방법 가이드를 시작 하려면 하나를 만드세요.

## <a name="scale-compute-and-storage"></a>계산 및 저장소 크기 조정

다음 명령을 사용 하 여 계산 계층, vCores 및 저장소를 쉽게 확장할 수 있습니다. 수행할 수 있는 모든 서버 작업을 볼 수 있습니다 [az mysql 신축 서버 업데이트](/cli/azure/mysql/flexible-server#az_mysql_flexible_server_update)

```azurecli-interactive
az mysql flexible-server update --resource-group myresourcegroup --name mydemoserver --sku-name Standard_D4ds_v4 --storage-size 6144
```

위의 인수에 대한 세부 정보는 다음과 같습니다.

**설정** | **샘플 값** | **설명**
---|---|---
name | mydemoserver | 고유한 Azure Database for MySQL 서버 이름을 입력합니다. 서버 이름은 소문자, 숫자 및 하이픈(-) 문자만 포함할 수 있으며, 3-63자여야 합니다.
resource-group | myresourcegroup | Azure 리소스 그룹의 이름을 입력합니다.
sku-name|Standard_D4ds_v4|계산 계층 및 크기의 이름을 입력 합니다. 는 줄임의 {VM size} Standard_ 규칙을 따릅니다. 자세한 내용은 [가격 책정 계층](../concepts-pricing-tiers.md)을 참조하세요.
storage-size | 6144 | 서버의 스토리지 용량입니다(단위는 메가바이트). 최소 5120 및 1024 증분 단위로 증가 합니다.

> [!Important]
> - 저장소를 확장할 수 있습니다 (그러나 저장소 크기를 줄일 수 없음).


## <a name="manage-mysql-databases-on-a-server"></a>서버에서 MySQL 데이터베이스를 관리 합니다.
이러한 명령 중 하나를 사용 하 여 서버에 있는 데이터베이스의 데이터베이스 속성을 만들고, 삭제 하 고, 나열 하 고, 볼 수 있습니다.

| cmdlet | 사용| Description |
| --- | ---| --- |
|[az mysql 유연한 서버 db 만들기](/cli/azure/mysql/flexible-server/db#az_mysql_flexible_server_db_create)|```az mysql flexible-server db create -g myresourcegroup -s mydemoserver -n mydatabasename``` |데이터베이스 만들기|
|[az mysql 신축 서버 db delete](/cli/azure/mysql/flexible-server/db#az_mysql_flexible_server_db_delete)|```az mysql flexible-server db delete -g myresourcegroup -s mydemoserver -n mydatabasename```|서버에서 데이터베이스를 삭제 합니다. 이 명령은 서버를 삭제 하지 않습니다. |
|[az mysql 신축 서버 db 목록](/cli/azure/mysql/flexible-server/db#az_mysql_flexible_server_db_list)|```az mysql flexible-server db list -g myresourcegroup -s mydemoserver```|서버에 있는 모든 데이터베이스를 나열 합니다.|
|[az mysql 신축 서버 db 표시](/cli/azure/mysql/flexible-server/db#az_mysql_flexible_server_db_show)|```az mysql flexible-server db show -g myresourcegroup -s mydemoserver -n mydatabasename```|데이터베이스에 대 한 자세한 정보를 표시 합니다.|

## <a name="update-admin-password"></a>관리자 암호 업데이트
이 명령을 사용 하 여 관리자 역할의 암호를 변경할 수 있습니다.
```azurecli-interactive
az mysql flexible-server update --resource-group myresourcegroup --name mydemoserver --admin-password <new-password>
```

> [!Important]
>  암호는 최소 8 자, 최대 128 자 인지 확인 합니다.
> 암호는 영어 대문자, 영어 소문자, 숫자 및 영숫자가 아닌 문자 범주 중 세 가지에 해당 하는 문자를 포함 해야 합니다.

## <a name="delete-a-server"></a>서버 삭제
MySQL의 유연한 서버를 삭제 하려는 경우 [az MySQL 신축-server server delete](/cli/azure/mysql/flexible-server#az_mysql_flexible_server_delete) 명령을 실행할 수 있습니다.

```azurecli-interactive
az mysql flexible-server delete --resource-group myresourcegroup --name mydemoserver
```

## <a name="next-steps"></a>다음 단계
- [서버를 시작 또는 중지 하는 방법 알아보기](how-to-stop-start-server-portal.md)
- [가상 네트워크를 관리 하는 방법 알아보기](how-to-manage-virtual-network-cli.md)
- [연결 문제 해결](how-to-troubleshoot-common-connection-issues.md)
- [방화벽 만들기 및 관리](how-to-manage-firewall-cli.md)