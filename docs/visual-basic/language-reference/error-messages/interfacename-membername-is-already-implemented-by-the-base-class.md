---
title: "&quot;&lt;interfacename&gt;.&lt; nome do membro&gt;&quot;já foi implementado pela classe base&quot;&lt;baseclassname&gt;&quot;. Reimplementação de &lt;tipo&gt; assumido | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42015
- bc42015
dev_langs:
- VB
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
caps.latest.revision: 12
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d792485f13e2b675858d82aa7219670a17fd974e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a><span data-ttu-id="d0e50-103">'&lt;interfacename&gt;.&lt; nome do membro&gt;'já foi implementado pela classe base'&lt;baseclassname&gt;'.</span><span class="sxs-lookup"><span data-stu-id="d0e50-103">&#39;&lt;interfacename&gt;.&lt;membername&gt;&#39; is already implemented by the base class &#39;&lt;baseclassname&gt;&#39;.</span></span> <span data-ttu-id="d0e50-104">Reimplementação de &lt;tipo&gt; assumido</span><span class="sxs-lookup"><span data-stu-id="d0e50-104">Re-implementation of &lt;type&gt; assumed</span></span>
<span data-ttu-id="d0e50-105">Uma propriedade, procedimento ou evento em uma classe derivada usa um `Implements` cláusula especificando um membro de interface que já é implementado na classe base.</span><span class="sxs-lookup"><span data-stu-id="d0e50-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>  
  
 <span data-ttu-id="d0e50-106">Uma classe derivada pode reimplementar um membro de interface que é implementado pela classe base.</span><span class="sxs-lookup"><span data-stu-id="d0e50-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="d0e50-107">Isso não é o mesmo que substituir a implementação da classe base.</span><span class="sxs-lookup"><span data-stu-id="d0e50-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="d0e50-108">Para obter mais informações, consulte [implementa](../../../visual-basic/language-reference/statements/implements-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d0e50-108">For more information, see [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).</span></span>  
  
 <span data-ttu-id="d0e50-109">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="d0e50-109">By default, this message is a warning.</span></span> <span data-ttu-id="d0e50-110">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d0e50-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d0e50-111">**ID do erro:** BC42015</span><span class="sxs-lookup"><span data-stu-id="d0e50-111">**Error ID:** BC42015</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d0e50-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d0e50-112">To correct this error</span></span>  
  
-   <span data-ttu-id="d0e50-113">Se você pretende reimplementar o membro de interface, você não precisa realizar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="d0e50-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="d0e50-114">Código em sua classe derivada acessa o membro reimplementedo, a menos que você use o `MyBase` palavra-chave para acessar a implementação da classe base.</span><span class="sxs-lookup"><span data-stu-id="d0e50-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>  
  
-   <span data-ttu-id="d0e50-115">Se você não pretende reimplementar o membro de interface, remova o `Implements` cláusula da declaração de propriedade, procedimento ou evento.</span><span class="sxs-lookup"><span data-stu-id="d0e50-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0e50-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0e50-116">See Also</span></span>  
 [<span data-ttu-id="d0e50-117">Interfaces</span><span class="sxs-lookup"><span data-stu-id="d0e50-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
