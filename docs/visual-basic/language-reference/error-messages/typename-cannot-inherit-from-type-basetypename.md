---
title: "&quot;&lt;typename&gt;&quot; não pode herdar de &lt;tipo&gt; &quot;&lt;NomeDoTipoBase&gt;&quot; porque ele expande o acesso da base de &lt;tipo&gt; fora do assembly | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30910
- bc30910
dev_langs:
- VB
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
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
ms.openlocfilehash: fc6d4b7f345338b46e0a71ab0752507d1e163acf
ms.lasthandoff: 03/13/2017

---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a>'&lt;typename&gt;' não pode herdar de &lt;tipo&gt; '&lt;NomeDoTipoBase&gt;' porque ele expande o acesso da base de &lt;tipo&gt; fora do assembly
Uma classe ou interface herda de uma classe base ou interface, mas tem um nível de acesso menos restritivo.  
  
 Por exemplo, um `Public` interface herda de uma `Friend` interface, ou um `Protected` classe herda de uma `Private` classe. Isso expõe a classe base ou interface para acesso além do nível desejado.  
  
 **ID do erro:** BC30910  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Altere o nível de acesso da classe derivada ou interface seja pelo menos tão restritivo quanto da classe base ou interface.  
  
     -ou-  
  
-   Se você exigir o nível de acesso menos restritivo, remova o `Inherits` instrução. Você não pode herdar de uma interface ou classe base mais restrito.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Instrução interface](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
