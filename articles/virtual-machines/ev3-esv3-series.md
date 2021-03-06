---
title: Ev3 시리즈 및 Esv3 시리즈
description: Ev3 및 Esv3 시리즈 Vm에 대 한 사양입니다.
author: DavidCBerry13
ms.service: virtual-machines
ms.subservice: sizes
ms.topic: conceptual
ms.date: 09/22/2020
ms.author: daberry
ms.openlocfilehash: 250223c5c15a0179fe105e66e7004f8920c5eb34
ms.sourcegitcommit: fb3c846de147cc2e3515cd8219d8c84790e3a442
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92637618"
---
# <a name="ev3-and-esv3-series"></a>Ev3 및 Esv3 시리즈

Ev3 및 Esv3 시리즈는 Intel® Xeon® 플래티넘 827272CL (Cascade Lake)에서 실행 됩니다. 또는 하이퍼 스레드 구성에서 Intel® Xeon® 8171M 2.1 GHz (Skylake) 또는 Intel® Xeon® E5-2673 v4 2.3 GHz (Broadwell) 프로세서를 사용 하 여 대부분의 범용 워크 로드에 대해 더 나은 가치를 제공 하 고 Ev3를 대부분의 다른 클라우드의 범용 Vm과 맞춥니다.  하이퍼 스레딩으로 이동하기 위해 디스크 및 네트워크 제한이 코어 단위로 조정되는 동안 메모리가 확장되었습니다(7GiB/vCPU에서 8GiB/vCPU로). Ev3는 D/Dv2 제품군의 상위 메모리 VM 크기에 대한 후속 시리즈입니다.

## <a name="ev3-series"></a>Ev3 시리즈

Ev3 시리즈 인스턴스는 Intel® Xeon® 플래티넘 8272CL (케스케이드 Lake), Intel® Xeon® 8171M 2.1 g h z (Skylake) 또는 Intel® Xeon® E5-2673 v4 2.3 GHz (Broadwell) 프로세서 및 기능 Intel 터보 부스트 기술 2.0에서 실행 됩니다. Ev3 시리즈 인스턴스는 메모리 집약적 엔터프라이즈 애플리케이션에 적합합니다.

데이터 디스크 스토리지는 가상 머신과 별도로 비용이 청구됩니다. Premium Storage 디스크를 사용하려면 ESv3 크기를 사용합니다. ESv3 크기의 가격 및 요금 청구 기준은 Ev3 시리즈와 동일합니다.

Ev3 시리즈 VM의 기능 Intel® Hyper-Threading 기술입니다.

[Acu](acu.md): 160-190<br>
[Premium Storage](premium-storage-performance.md): 지원 되지 않음<br>
[Premium Storage 캐싱](premium-storage-performance.md): 지원 되지 않음<br>
[실시간 마이그레이션](maintenance-and-updates.md): 지원 됨<br>
[메모리 보존 업데이트](maintenance-and-updates.md): 지원 됨<br>
[VM 생성 지원](generation-2.md): 1 세대<br>
<br>

| 크기 | vCPU | 메모리: GiB | 임시 스토리지(SSD) GiB | 최대 데이터 디스크 수 | 최대 임시 스토리지 처리량: IOPS/읽기 MBps/쓰기 MBps | 최대 NIC 수/네트워크 대역폭 |
|---|---|---|---|---|---|---|
| Standard_E2_v3  | 2  | 16  | 50   | 4  | 3000/46/23     | 2/1000  |
| Standard_E4_v3  | 4  | 32  | 100  | 8  | 6000/93/46     | 2/2000  |
| Standard_E8_v3  | 8  | 64  | 200  | 16 | 12000/187/93   | 4/4000  |
| Standard_E16_v3 | 16 | 128 | 400  | 32 | 24000/375/187  | 8/8000  |
| Standard_E20_v3 | 20 | 160 | 500  | 32 | 30000/469/234  | 8/10000 |
| Standard_E32_v3 | 32 | 256 | 800  | 32 | 48000/750/375  | 8/16000 |
| Standard_E48_v3 | 48 | 384 | 1200 | 32 | 96000/1000/500 | 8/24000 |
| Standard_E64_v3 | 64 | 432 | 1600 | 32 | 96000/1000/500 | 8/30000 |
| Standard_E64i_v3 <sup>1, 2</sup> | 64 | 432 | 1600 | 32 | 96000/1000/500 | 8/30000 |

<sup>1</sup> 제한 된 코어 크기를 사용할 수 있습니다.

<sup>2</sup> 인스턴스는 단일 고객 전용의 하드웨어에 격리되어 있습니다.

## <a name="esv3-series"></a>Esv3 시리즈

Esv3 시리즈 인스턴스는 Intel® Xeon® 플래티넘 8272CL (케스케이드 Lake), Intel® Xeon® 8171M 2.1 g h z (Skylake) 또는 Intel® Xeon® E5-2673 v4 2.3 GHz (Broadwell) 프로세서에서 실행 되며, Intel 터보 부스트 기술 2.0을 사용 하 고 premium storage를 사용 합니다. Esv3 시리즈 인스턴스는 메모리를 많이 사용 하는 엔터프라이즈 응용 프로그램에 적합 합니다.

Esv3 시리즈 VM의 기능 Intel® Hyper-Threading 기술입니다.

[Acu](acu.md): 160-190<br>
[Premium Storage](premium-storage-performance.md): 지원 됨<br>
[Premium Storage 캐싱](premium-storage-performance.md): 지원 됨<br>
[실시간 마이그레이션](maintenance-and-updates.md): 지원 됨<br>
[메모리 보존 업데이트](maintenance-and-updates.md): 지원 됨<br>
[VM 생성 지원](generation-2.md): 1 세대 및 2 세대<br>
<br>

| 크기 | vCPU | 메모리: GiB | 임시 스토리지(SSD) GiB | 최대 데이터 디스크 수 | 최대 캐시 및 임시 저장소 처리량: IOPS/MBps (GiB의 캐시 크기) | 버스트 캐시 및 임시 저장소 처리량: IOPS/MBps<sup>3</sup> | 캐시되지 않은 최대 디스크 처리량: IOPS/MBps |  버스트 캐시 되지 않은 디스크 처리량: IOPS/MBps<sup>3</sup>| 최대 Nic/예상 네트워크 대역폭 (Mbps) |
|---|---|---|---|---|---|---|---|---|---|
| Standard_E2s_v3                | 2  | 16  | 32  | 4  | 4000/32 (50)       | 4000/100    | 3200/48    | 4000/100 | 2/1000 |
| Standard_E4s_v3 <sup>1</sup>   | 4  | 32  | 64  | 8  | 8000/64 (100)      | 8000/200    | 6400/96    | 8000/200 | 2/2000 |
| Standard_E8s_v3 <sup>1</sup>   | 8  | 64  | 128 | 16 | 16000/128 (200)    | 16000/400   | 12800/192  | 16000/400 | 4/4000 |
| Standard_E16s_v3 <sup>1</sup>  | 16 | 128 | 256 | 32 | 32000/256 (400)    | 32000/800   | 25600/384  | 32000/800 | 8/8000 |
| Standard_E20s_v3               | 20 | 160 | 320 | 32 | 40000/320 (400)    | 40000/1000  | 32000/480  | 40000/1000 | 8/10000 |
| Standard_E32s_v3 <sup>1</sup>  | 32 | 256 | 512 | 32 | 64000/512 (800)    | 64000/1600  | 51200/768  | 64000/1600 | 8/16000 |
| Standard_E48s_v3 <sup>1</sup>  | 48 | 384 | 768 | 32 | 96000/768 (1200)   | 96000/2000  | 76800/1152 | 80000/2000 | 8/24000 |
| Standard_E64s_v3 <sup>1</sup>  | 64 | 432 | 864 | 32 | 128000/1024 (1600) | 128000/2000 | 80000/1200 | 80000/2000 | 8/30000 |
| Standard_E64is_v3 <sup>2</sup> | 64 | 432 | 864 | 32 | 128000/1024 (1600) | 128000/2000 | 80000/1200 | 80000/2000 | 8/30000 |

<sup>1</sup> 제한 된 코어 크기를 사용할 수 있습니다.

<sup>2</sup> 인스턴스는 단일 고객 전용의 하드웨어에 격리되어 있습니다.

<sup>3</sup> Esv3 시리즈 vm은 디스크 성능을 [버스트](linux/disk-bursting.md) 하 고 한 번에 최대 30 분 동안 최대 버스트를 얻을 수 있습니다.

[!INCLUDE [virtual-machines-common-sizes-table-defs](../../includes/virtual-machines-common-sizes-table-defs.md)]

## <a name="other-sizes-and-information"></a>기타 크기 및 정보

- [범용](sizes-general.md)
- [메모리에 최적화](sizes-memory.md)
- [Storage에 최적화](sizes-storage.md)
- [GPU에 최적화](sizes-gpu.md)
- [고성능 컴퓨팅](sizes-hpc.md)
- [이전 세대](sizes-previous-gen.md)
- [요금 계산기](https://azure.microsoft.com/pricing/calculator/).
- 디스크 유형에 대 한 자세한 내용은 [Azure에서 사용할 수 있는 디스크 유형](disks-types.md) 을 참조 하세요.

## <a name="next-steps"></a>다음 단계

[ACU(Azure 컴퓨팅 단위)](acu.md)가 Azure SKU 간의 Compute 성능을 비교하는 데 어떻게 도움을 줄 수 있는지 알아봅니다.