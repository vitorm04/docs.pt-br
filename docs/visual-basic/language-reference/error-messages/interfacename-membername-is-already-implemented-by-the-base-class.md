---
title: "&#39; &lt;interfacename&gt;.&lt; membername&gt;&#39; já foi implementado pela classe base &#39;&lt; baseclassname&gt;&#39;. Reimplementação de &lt;tipo&gt; assumido"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords: BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 69884ed567e0046da5cf5c51b3e83e57e890d49f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a><span data-ttu-id="7933e-103">&#39; &lt;interfacename&gt;.&lt; membername&gt;&#39; já foi implementado pela classe base &#39;&lt; baseclassname&gt;&#39;.</span><span class="sxs-lookup"><span data-stu-id="7933e-103">&#39;&lt;interfacename&gt;.&lt;membername&gt;&#39; is already implemented by the base class &#39;&lt;baseclassname&gt;&#39;.</span></span> <span data-ttu-id="7933e-104">Reimplementação de &lt;tipo&gt; assumido</span><span class="sxs-lookup"><span data-stu-id="7933e-104">Re-implementation of &lt;type&gt; assumed</span></span>
<span data-ttu-id="7933e-105">Uma propriedade, procedimento ou evento em uma classe derivada usa um `Implements` cláusula especificando um membro de interface que já é implementado na classe base.</span><span class="sxs-lookup"><span data-stu-id="7933e-105">A property, procedure, or event in a derived class uses an `Implements` clause specifying an interface member that is already implemented in the base class.</span></span>  
  
 <span data-ttu-id="7933e-106">Uma classe derivada pode reimplementar um membro de interface é implementado por sua classe base.</span><span class="sxs-lookup"><span data-stu-id="7933e-106">A derived class can reimplement an interface member that is implemented by its base class.</span></span> <span data-ttu-id="7933e-107">Isso não é o mesmo que substituir a implementação da classe base.</span><span class="sxs-lookup"><span data-stu-id="7933e-107">This is not the same as overriding the base class implementation.</span></span> <span data-ttu-id="7933e-108">Para obter mais informações, consulte [implementa](../../../visual-basic/language-reference/statements/implements-clause.md).</span><span class="sxs-lookup"><span data-stu-id="7933e-108">For more information, see [Implements](../../../visual-basic/language-reference/statements/implements-clause.md).</span></span>  
  
 <span data-ttu-id="7933e-109">Por padrão, esta mensagem é um aviso.</span><span class="sxs-lookup"><span data-stu-id="7933e-109">By default, this message is a warning.</span></span> <span data-ttu-id="7933e-110">Para obter informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="7933e-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="7933e-111">**ID do erro:** BC42015</span><span class="sxs-lookup"><span data-stu-id="7933e-111">**Error ID:** BC42015</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7933e-112">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="7933e-112">To correct this error</span></span>  
  
-   <span data-ttu-id="7933e-113">Se você pretende reimplementar o membro de interface, você não precisa realizar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="7933e-113">If you intend to reimplement the interface member, you do not need to take any action.</span></span> <span data-ttu-id="7933e-114">O código em sua classe derivada acessa o membro reimplementedo, a menos que você use o `MyBase` palavra-chave para acessar a implementação da classe base.</span><span class="sxs-lookup"><span data-stu-id="7933e-114">Code in your derived class accesses the reimplemented member unless you use the `MyBase` keyword to access the base class implementation.</span></span>  
  
-   <span data-ttu-id="7933e-115">Se você não pretende reimplementar o membro de interface, remova o `Implements` cláusula na declaração de propriedade, procedimento ou evento.</span><span class="sxs-lookup"><span data-stu-id="7933e-115">If you do not intend to reimplement the interface member, remove the `Implements` clause from the property, procedure, or event declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7933e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7933e-116">See Also</span></span>  
 [<span data-ttu-id="7933e-117">Interfaces</span><span class="sxs-lookup"><span data-stu-id="7933e-117">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
