---
title: '#Diretiva de região (Visual Basic)'
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
ms.openlocfilehash: 204b53751fce4f9a3e038ae7c44634522d54657c
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264175"
---
# <a name="region-directive"></a>Diretiva #Region
Recolhe e oculta seções de código em arquivos do Visual Basic.  
  
## <a name="syntax"></a>Sintaxe  

```vb
#Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`identifier_string`|Necessário. Cadeia de caracteres que atua como o título de uma região quando ele estiver recolhido. Regiões recolhidas por padrão.|  
|`#End Region`|Encerra o `#Region` bloco.|  
  
## <a name="remarks"></a>Comentários  
 Use o `#Region` diretiva para especificar um bloco de código para expandir ou recolher ao usar o recurso de estrutura de tópicos do Editor de código do Visual Studio. Você pode colocar, ou *aninhar*, regiões em outras regiões para agrupar regiões semelhantes.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o `#Region` diretiva.  
  
 [!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Diretivas #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Estrutura de tópicos](/visualstudio/ide/outlining)  
 [Como recolher e ocultar seções do código](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
