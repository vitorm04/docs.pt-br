---
title: "&#39; &lt;typename&gt;&#39; não pode herdar de &lt;tipo&gt; &#39;&lt; NomeDoTipoBase&gt;&#39; porque ele expande o acesso da base de &lt;tipo&gt; fora do assembly"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords: BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d01981d3136968ae2534539b8eccab4c5c535fbc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a>&#39; &lt;typename&gt;&#39; não pode herdar de &lt;tipo&gt; &#39;&lt; NomeDoTipoBase&gt;&#39; porque ele expande o acesso da base de &lt;tipo&gt; fora do assembly
Uma classe ou interface herda de uma classe base ou interface, mas tem um nível de acesso menos restritivo.  
  
 Por exemplo, um `Public` interface herda de uma `Friend` interface, ou um `Protected` classe herda de uma `Private` classe. Isso expõe a classe base ou interface para acesso além do nível desejado.  
  
 **ID do erro:** BC30910  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Altere o nível de acesso da classe derivada ou interface para que seja pelo menos tão restritivo quanto da classe base ou interface.  
  
     -ou-  
  
-   Se você precisar que o nível de acesso menos restritivo, remova o `Inherits` instrução. Você não pode herdar de uma interface ou classe base mais restrito.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
