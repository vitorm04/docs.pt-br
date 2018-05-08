---
title: -highentropyva (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fef3f922d3089eaca1762ffe35fa38cfe94baf22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="-highentropyva-visual-basic"></a>-highentropyva (Visual Basic)
Indica se um executável de 64 bits ou um executável que é marcado pelo [/platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) opção de compilador dá suporte à alta entropia endereço espaço Layout aleatória (ASLR).  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Opcional. A opção está desativada por padrão, ou se você especificar `-highentropyva-`. A opção está ativada e se você especificar `-highentropyva` ou `-highentropyva+`.  
  
## <a name="remarks"></a>Comentários  
 Se você especificar essa opção, as versões compatíveis do kernel do Windows podem usar níveis mais altos de entropia ao kernel aleatoriamente o layout do espaço de endereço de um processo como parte de ASLR. Se o kernel usa níveis mais altos de entropia, um número maior de endereços pode ser alocado para regiões de memória, como pilhas e heaps. Como resultado, é mais difícil adivinhar a localização de uma região específica da memória.  
  
 Quando a opção está ativada, o executável de destino e todos os módulos no qual ele depende deve ser capaz de lidar com valores de ponteiro que são maiores do que 4 gigabytes (GB) quando esses módulos estão sendo executados como processos de 64 bits.  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
