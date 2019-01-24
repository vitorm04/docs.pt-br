---
title: '&#39;&lt;TypeName&gt; &#39; não pode herdar de &lt;tipo&gt; &#39; &lt;basetypename&gt; &#39; porque ele expande o acesso da base de &lt;tipo&gt; fora do assembly'
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: 108025132bdd0fa86df5ed142aaa39c7b7e18062
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556477"
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a>&#39;&lt;TypeName&gt; &#39; não pode herdar de &lt;tipo&gt; &#39; &lt;basetypename&gt; &#39; porque ele expande o acesso da base de &lt;tipo&gt; fora do assembly
Uma classe ou interface herda de uma classe base ou interface, mas tem um nível de acesso menos restritivo.  
  
 Por exemplo, uma `Public` interface herda de uma `Friend` interface, ou um `Protected` classe herda de uma `Private` classe. Isso expõe a classe base ou interface para acesso além do nível desejado.  
  
 **ID do erro:** BC30910  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Altere o nível de acesso da classe derivada ou interface seja pelo menos tão restritivo quanto da classe base ou interface.  
  
     -ou-  
  
-   Se você exigir o nível de acesso menos restritivo, remova o `Inherits` instrução. Você não pode herdar de uma classe base mais restrito ou interface.  
  
## <a name="see-also"></a>Consulte também
- [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Instrução Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Instrução Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Níveis de acesso no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
