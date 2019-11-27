---
title: Esta matriz é fixa ou está temporariamente bloqueada
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: 8d5e4add2d92a575126fb934ac3874a2e37685f5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350784"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>Esta matriz é fixa ou está temporariamente bloqueada (Visual Basic)
Esse erro tem as seguintes causas possíveis:  
  
- Usando `ReDim` para alterar o número de elementos de uma matriz de tamanho fixo.  
  
- Redimensionamento de uma matriz dinâmica em nível de módulo, na qual um elemento foi passado como um argumento para um procedimento. Se um elemento for passado, a matriz será bloqueada para evitar a desalocação de memória para o parâmetro de referência no procedimento.  
  
- A tentativa de atribuir um valor a uma variável `Variant` que contém uma matriz, mas o `Variant` está bloqueado no momento.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Torne a matriz original dinâmica, em vez de corrigida, declarando-a com `ReDim` (se a matriz for declarada dentro de um procedimento) ou declarando-a sem especificar o número de elementos (se a matriz for declarada no nível do módulo.  
  
2. Determine se você realmente precisa passar o elemento, pois ele está visível em todos os procedimentos no módulo.  
  
3. Determine o que está bloqueando o `Variant` e corrija-o.  
  
## <a name="see-also"></a>Consulte também

- [Matrizes](../../../visual-basic/programming-guide/language-features/arrays/index.md)
