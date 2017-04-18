---
title: Use &quot;FileGetObject&quot; em vez de &quot;FileGet&quot; quando usar argumento do tipo &quot;Object&quot; | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
ms.assetid: 090b8088-895a-482a-9362-606596bac304
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 26c32e497b072834ffe12ea0501d5b859647739b
ms.lasthandoff: 03/13/2017

---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a>Use 'FileGetObject' em vez de 'FileGet' quando usar argumento do tipo 'Object'
O `FileGet` método inclui um argumento do tipo `Object`. `FileGetObject`deve ser usado no lugar de `FileGet` para evitar ambiguidades.  
  
 Observe que a funcionalidade oferecida por `My.Computer.Filesystem` oferece maior facilidade de uso e desempenho que seja `FileGet` ou `FileGetObject`.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Substitua `FileGet` por `FileGetObject`.  
  
2.  Conversão de `Object` argumento para um tipo mais específico.  
  
## <a name="see-also"></a>Consulte também  
 [NÃO está em compilação: Função FileGetObject](http://msdn.microsoft.com/en-us/3eda786b-d1ee-4b44-9dd7-0ea6bff072c0)   
 [Objeto My.Computer.FileSystem](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)
