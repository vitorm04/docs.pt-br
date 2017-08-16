---
title: "#Diretiva de região | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Region
- vb.#Region
dev_langs:
- VB
helpviewer_keywords:
- Visual Basic compiler, compiler directives
- '#region directive'
- region directive (#region)
- '#Region keyword'
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1c429602a7eee27944f58256992879d25d533d34
ms.lasthandoff: 03/13/2017

---
# <a name="region-directive"></a>#Diretiva de região
Recolhe e oculta seções de código em arquivos do Visual Basic.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
      #Region "identifier_string"  
#End Region  
```  
  
## <a name="parts"></a>Partes  
  
|Termo|Definição|  
|---|---|  
|`identifier_string`|Necessário. Cadeia de caracteres que atua como o título de uma região quando ele estiver recolhido. Regiões estão recolhidas por padrão.|  
|`#End Region`|Encerra o `#Region` bloco.|  
  
## <a name="remarks"></a>Comentários  
 Use o `#Region` diretiva para especificar um bloco de código para expandir ou recolher ao usar o recurso de estruturação do Editor de código do Visual Studio. Você pode colocar, ou *aninhar*, regiões em outras regiões para agrupar regiões semelhantes.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa a `#Region` diretiva.  
  
 [!code-vb[VbVbalrConditionalComp n º&4;](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [#If... Then... #Else diretivas](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [Estrutura de tópicos](https://docs.microsoft.com/visualstudio/ide/outlining)   
 [Como recolher e ocultar seções do código](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)
