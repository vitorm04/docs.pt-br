---
title: '#Diretiva Region'
ms.date: 07/20/2015
f1_keywords:
- vb.Region
- vb.#Region
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword [Visual Basic]'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
ms.openlocfilehash: 4cf9b103486378d001b588aa285f590980b51bb8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343787"
---
# <a name="region-directive"></a>Diretiva #Region

Recolhe e oculta seções de código em Visual Basic arquivos.  
  
## <a name="syntax"></a>Sintaxe  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`identifier_string`|Necessária. Cadeia de caracteres que atua como o título de uma região quando ela é recolhida. As regiões são recolhidas por padrão.|  
|`#End Region`|Encerra o bloco de `#Region`.|  
  
## <a name="remarks"></a>Comentários  

 Use a diretiva `#Region` para especificar um bloco de código para expandir ou recolher ao usar o recurso de estrutura de tópicos do editor de Visual Studio Code. Você pode posicionar ou *aninhar*regiões em outras regiões para agrupar regiões semelhantes.  
  
## <a name="example"></a>Exemplo  

 Este exemplo usa a diretiva `#Region`.  
  
 [!code-vb[VbVbalrConditionalComp#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>Consulte também

- [Diretivas #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Estrutura de tópicos](/visualstudio/ide/outlining)
- [Como recolher e ocultar seções do código](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
