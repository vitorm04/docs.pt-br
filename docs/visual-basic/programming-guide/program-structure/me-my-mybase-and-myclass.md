---
title: Me, My, MyBase e MyClass no Visual Basic
ms.date: 07/20/2015
f1_keywords:
- MyClass
- vb.Me
- MyBase
- vb.MyBase
- Me
- vb.MyClass
- vb.This
- vb.My
helpviewer_keywords:
- My object
- self-reference [Visual Basic], Me keyword
- MyClass keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], relationship to similar programming elements
- Me keyword [Visual Basic], referring to the current instance of an object
- Me keyword [Visual Basic]
- self-reference
- current instance [Visual Basic], Me keyword
- MyBase keyword [Visual Basic], relationship to similar programming elements
ms.assetid: f8e241ae-b1ed-4886-9aa0-08c632154029
ms.openlocfilehash: a8df6e48fd5bce9bb28d8aef7e031f36741ad0ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050474"
---
# <a name="me-my-mybase-and-myclass-in-visual-basic"></a><span data-ttu-id="cdc44-102">Me, My, MyBase e MyClass no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cdc44-102">Me, My, MyBase, and MyClass in Visual Basic</span></span>
<span data-ttu-id="cdc44-103">`Me`, `My`, `MyBase`, e `MyClass` no Visual Basic têm nomes semelhantes, mas diferentes finalidades.</span><span class="sxs-lookup"><span data-stu-id="cdc44-103">`Me`, `My`, `MyBase`, and `MyClass` in Visual Basic have similar names, but different purposes.</span></span> <span data-ttu-id="cdc44-104">Este tópico descreve cada uma dessas entidades para distingui-los.</span><span class="sxs-lookup"><span data-stu-id="cdc44-104">This topic describes each of these entities in order to distinguish them.</span></span>  
  
## <a name="me"></a><span data-ttu-id="cdc44-105">Me</span><span class="sxs-lookup"><span data-stu-id="cdc44-105">Me</span></span>  
 <span data-ttu-id="cdc44-106">O `Me` palavra-chave fornece uma maneira para referir-se à instância específica de uma classe ou estrutura na qual o código está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="cdc44-106">The `Me` keyword provides a way to refer to the specific instance of a class or structure in which the code is currently executing.</span></span> <span data-ttu-id="cdc44-107">`Me` se comporta como uma variável de objeto ou uma variável de estrutura referindo-se à instância atual.</span><span class="sxs-lookup"><span data-stu-id="cdc44-107">`Me` behaves like either an object variable or a structure variable referring to the current instance.</span></span> <span data-ttu-id="cdc44-108">Usando `Me` é particularmente útil para passar informações sobre a instância em execução no momento de uma classe ou estrutura para um procedimento em outra classe, estrutura ou módulo.</span><span class="sxs-lookup"><span data-stu-id="cdc44-108">Using `Me` is particularly useful for passing information about the currently executing instance of a class or structure to a procedure in another class, structure, or module.</span></span>  
  
 <span data-ttu-id="cdc44-109">Por exemplo, suponha que você tem o procedimento a seguir em um módulo.</span><span class="sxs-lookup"><span data-stu-id="cdc44-109">For example, suppose you have the following procedure in a module.</span></span>  
  
```  
Sub ChangeFormColor(FormName As Form)  
   Randomize()  
   FormName.BackColor = Color.FromArgb(Rnd() * 256, Rnd() * 256, Rnd() * 256)  
End Sub  
```  
  
 <span data-ttu-id="cdc44-110">Você pode chamar esse procedimento e passar a instância atual do <xref:System.Windows.Forms.Form> classe como um argumento usando a instrução a seguir.</span><span class="sxs-lookup"><span data-stu-id="cdc44-110">You can call this procedure and pass the current instance of the <xref:System.Windows.Forms.Form> class as an argument by using the following statement.</span></span>  
  
```  
ChangeFormColor(Me)  
```  
  
## <a name="my"></a><span data-ttu-id="cdc44-111">Meu</span><span class="sxs-lookup"><span data-stu-id="cdc44-111">My</span></span>  
 <span data-ttu-id="cdc44-112">O `My` recurso fornece acesso rápido e intuitivo para um número de [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes, permitindo que o usuário do Visual Basic interagir com o computador, aplicativo, configurações, recursos e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="cdc44-112">The `My` feature provides easy and intuitive access to a number of [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] classes, enabling the Visual Basic user to interact with the computer, application, settings, resources, and so on.</span></span>  
  
## <a name="mybase"></a><span data-ttu-id="cdc44-113">MyBase</span><span class="sxs-lookup"><span data-stu-id="cdc44-113">MyBase</span></span>  
 <span data-ttu-id="cdc44-114">O `MyBase` palavra-chave se comporta como uma variável de objeto consultando a classe base da instância atual de uma classe.</span><span class="sxs-lookup"><span data-stu-id="cdc44-114">The `MyBase` keyword behaves like an object variable referring to the base class of the current instance of a class.</span></span> <span data-ttu-id="cdc44-115">`MyBase` normalmente é usado para acessar membros de classe base que são substituídos ou sombreados em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="cdc44-115">`MyBase` is commonly used to access base class members that are overridden or shadowed in a derived class.</span></span> <span data-ttu-id="cdc44-116">`MyBase.New` é usado para chamar explicitamente um construtor de classe base de um construtor de classe derivada.</span><span class="sxs-lookup"><span data-stu-id="cdc44-116">`MyBase.New` is used to explicitly call a base class constructor from a derived class constructor.</span></span>  
  
## <a name="myclass"></a><span data-ttu-id="cdc44-117">MyClass</span><span class="sxs-lookup"><span data-stu-id="cdc44-117">MyClass</span></span>  
 <span data-ttu-id="cdc44-118">O `MyClass` palavra-chave se comporta como uma variável de objeto referindo-se à instância atual de uma classe como originalmente implementada.</span><span class="sxs-lookup"><span data-stu-id="cdc44-118">The `MyClass` keyword behaves like an object variable referring to the current instance of a class as originally implemented.</span></span> <span data-ttu-id="cdc44-119">`MyClass` é semelhante à `Me`, mas todas as chamadas de método nele são tratadas como se fosse o método `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="cdc44-119">`MyClass` is similar to `Me`, but all method calls on it are treated as if the method were `NotOverridable`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdc44-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdc44-120">See also</span></span>

- [<span data-ttu-id="cdc44-121">Noções Básicas de Herança</span><span class="sxs-lookup"><span data-stu-id="cdc44-121">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
