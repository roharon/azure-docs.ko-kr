---
title: '열 추가: 모듈 참조'
titleSuffix: Azure Machine Learning
description: 끌어서 놓기 Azure Machine Learning 디자이너에서 열 추가 모듈을 사용 하 여 두 데이터 집합을 연결 하는 방법을 알아봅니다.
services: machine-learning
ms.service: machine-learning
ms.subservice: core
ms.topic: reference
author: likebupt
ms.author: keli19
ms.date: 10/22/2019
ms.openlocfilehash: 36de827dff239dbeebc66e330a76b7a65fefb909
ms.sourcegitcommit: 7cc10b9c3c12c97a2903d01293e42e442f8ac751
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/06/2020
ms.locfileid: "93421960"
---
# <a name="add-columns-module"></a>열 추가 모듈

이 문서에서는 Azure Machine Learning 디자이너의 모듈을 설명 합니다.

이 모듈을 사용 하 여 두 데이터 집합을 연결 합니다. 지정 하는 두 데이터 집합의 모든 열을 입력으로 결합 하 여 단일 데이터 집합을 만듭니다. 세 개 이상의 데이터 집합을 연결 해야 하는 경우 **열 추가** 의 여러 인스턴스를 사용 합니다.



## <a name="how-to-configure-add-columns"></a>열 추가를 구성 하는 방법
1. 파이프라인에 **열 추가** 모듈을 추가 합니다.

2. 연결 하려는 두 데이터 집합을 연결 합니다. 세 개 이상의 데이터 집합을 결합 하려는 경우에는 여러 개의 **열** 을 조합 하 여 함께 사용할 수 있습니다.

    - 행 수가 다른 두 개의 열을 결합할 수 있습니다. 출력 데이터 집합은 작은 원본 열의 각 행에 대해 누락 된 값으로 채워집니다.

    - 추가할 개별 열을 선택할 수 없습니다. **열 추가** 를 사용 하는 경우 각 데이터 집합의 모든 열이 연결 됩니다. 따라서 열의 하위 집합만 추가 하려면 데이터 집합의 열 선택을 사용 하 여 원하는 열이 포함 된 데이터 집합을 만듭니다.

3. 파이프라인을 제출합니다.

### <a name="results"></a>결과
파이프라인이 실행 된 후 다음을 수행 합니다.

- 새 데이터 집합의 첫 번째 행을 보려면 **열 추가** 모듈을 마우스 오른쪽 단추로 클릭 하 고 시각화를 선택 합니다. 또는 모듈을 선택 하 고 오른쪽 패널의 **출력** 탭으로 전환 하 고 **포트 출력** 에서 히스토그램 아이콘을 클릭 하 여 결과를 시각화 합니다.

새 데이터 집합의 열 수는 두 입력 데이터 집합의 열 합과 같습니다.

입력 데이터 집합에 이름이 같은 열이 두 개 있으면 열 이름에 숫자 접미사가 추가 됩니다. 예를 들어 TargetOutcome 이라는 열이 두 개 있는 경우 왼쪽 열 이름이 TargetOutcome_1 변경 되 고 TargetOutcome_2 오른쪽 열의 이름이 바뀝니다.

## <a name="next-steps"></a>다음 단계

Azure Machine Learning에서 [사용 가능한 모듈 세트](module-reference.md)를 참조하세요. 