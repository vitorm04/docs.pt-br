---
title: Me, My, MyBase e MyClass no Visual Basic | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
dev_langs:
- VB
helpviewer_keywords:
- My object
- self-reference, Me keyword
- MyClass keyword, relationship to similar programming elements
- Me keyword, relationship to similar programming elements
- Me keyword, referring to the current instance of an object
- Me keyword
- self-reference
- current instance, Me keyword
- MyBase keyword, relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
caps.latest.revision: 15
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
ms.openlocfilehash: 3ba634eb28c25f47a0e88c856b916383b6ad15a2
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="41d8f-102">Me, My, MyBase e MyClass no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="41d8f-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="41d8f-103">`Me`, `My`, `MyBase`, e `MyClass` na [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] têm nomes semelhantes, mas diferentes finalidades.</span><span class="sxs-lookup"><span data-stu-id="41d8f-103">`Me`, `My`, `MyBase`, and `MyClass` in [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] have similar names, but different purposes.</span></span> <span data-ttu-id="41d8f-104">Este tópico descreve cada uma dessas entidades para diferenciá-los.</span><span class="sxs-lookup"><span data-stu-id="41d8f-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="41d8f-105">Eu</span><span class="sxs-lookup"><span data-stu-id="41d8f-105">Me</span></span>  
 <span data-ttu-id="41d8f-106">O `Me` palavra-chave fornece uma maneira de se referir à instância específica de uma classe ou estrutura na qual o código está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="41d8f-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="41d8f-107">`Me`se comporta como uma variável de objeto ou uma variável de estrutura referindo-se à instância atual.</span><span class="sxs-lookup"><span data-stu-id="41d8f-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="41d8f-108">Usando `Me` é particularmente útil para passar informações sobre a instância atualmente em execução de uma classe ou estrutura para um procedimento em outra classe, estrutura ou módulo.</span><span class="sxs-lookup"><span data-stu-id="41d8f-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="41d8f-109">Por exemplo, suponha que você tenha o procedimento a seguir em um módulo.</span><span class="sxs-lookup"><span data-stu-id="41d8f-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="41d8f-110">Você pode chamar esse procedimento e passar a instância atual do <xref:System.Windows.Forms.Form>classe como um argumento usando a instrução a seguir.</xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="41d8f-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="41d8f-111">Meu</span><span class="sxs-lookup"><span data-stu-id="41d8f-111">My</span></span>  
 <span data-ttu-id="41d8f-112">O `My` recurso fornece acesso fácil e intuitivo para um número de [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] classes, permitindo que o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] usuário interagir com o computador, aplicativos, configurações, recursos e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="41d8f-112">The `My` feature provides easy and intuitive access to a number of [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] classes, enabling the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="41d8f-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="41d8f-113">MyBase</span></span>  
 <span data-ttu-id="41d8f-114">O `MyBase` palavra-chave se comporta como uma variável de objeto consultando a classe base da instância atual de uma classe.</span><span class="sxs-lookup"><span data-stu-id="41d8f-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="41d8f-115">`MyBase`normalmente é usado para acessar membros de classe base que são substituídos ou sombreados em um classe derivada.</span><span class="sxs-lookup"><span data-stu-id="41d8f-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="41d8f-116">`MyBase.New`é usado para chamar um construtor de classe base de um construtor de classe derivada explicitamente.</span><span class="sxs-lookup"><span data-stu-id="41d8f-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="41d8f-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="41d8f-117">MyClass</span></span>  
 <span data-ttu-id="41d8f-118">O `MyClass` palavra-chave se comporta como uma variável de objeto referindo-se à instância atual de uma classe como implementada originalmente.</span><span class="sxs-lookup"><span data-stu-id="41d8f-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="41d8f-119">`MyClass`é semelhante ao `Me`, mas todas as chamadas de método nele são tratadas como se fosse o método `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="41d8f-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41d8f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41d8f-120">See Also</span></span>  
 [<span data-ttu-id="41d8f-121">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="41d8f-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
