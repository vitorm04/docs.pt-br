---
title: '&#39;&lt;InterfaceName&gt;.&lt; membername&gt; &#39; já foi implementado pela classe base &#39; &lt;baseclassname&gt;&#39;. Reimplementação de &lt;tipo&gt; assumido'
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 9054c293ede9db4637f23579407f2f76db29f2ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588964"
---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a>&#39;&lt;InterfaceName&gt;.&lt; membername&gt; &#39; já foi implementado pela classe base &#39; &lt;baseclassname&gt;&#39;. Reimplementação de &lt;tipo&gt; assumido
Uma propriedade, procedimento ou evento em uma classe derivada usa um `Implements` cláusula especificando um membro de interface que já é implementado na classe base.  
  
 Uma classe derivada pode reimplementar um membro de interface é implementado por sua classe base. Isso não é o mesmo que substituir a implementação da classe base. Para obter mais informações, consulte [implementa](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
 Por padrão, esta mensagem é um aviso. Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC42015  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Se você pretende reimplementar o membro de interface, você não precisa realizar nenhuma ação. O código em sua classe derivada acessa o membro reimplementedo, a menos que você use o `MyBase` palavra-chave para acessar a implementação da classe base.  
  
-   Se você não pretende reimplementar o membro de interface, remova o `Implements` cláusula na declaração de propriedade, procedimento ou evento.  
  
## <a name="see-also"></a>Consulte também  
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
