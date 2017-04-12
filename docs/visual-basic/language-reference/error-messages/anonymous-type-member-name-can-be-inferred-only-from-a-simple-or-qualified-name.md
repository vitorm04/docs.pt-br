---
title: "Nome do membro de tipo anônimo pode ser inferido somente de um nome simple ou qualificado sem argumentos | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36556
- bc36556
dev_langs:
- VB
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
caps.latest.revision: 8
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
ms.openlocfilehash: 55ca8f04359b65601ce95d7ed14e2e591de60989
ms.lasthandoff: 03/13/2017

---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>O nome do membro de tipo anônimo só pode ser inferido a partir de um nome simples ou qualificado sem argumentos
Não é possível inferir um nome de membro de tipo anônimo de uma expressão complexa.  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 Para obter mais informações sobre fontes de onde tipos anônimos podem e não é possível inferir nomes e tipos, consulte [como: inferir nomes de propriedade e tipos nas declarações de tipo anônimo](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
 **ID do erro:** BC36556  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Atribua a expressão a um nome de membro, conforme mostrado no código a seguir:  
  
    ```  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Tipos anônimos](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)   
 [Como inferir nomes e tipos de propriedade na declaração de tipo anônimo](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
