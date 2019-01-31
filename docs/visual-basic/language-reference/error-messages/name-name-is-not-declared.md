---
title: O nome '<name>' não é declarado
ms.date: 10/10/2018
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
ms.openlocfilehash: 3aadc49f91021409123550ba2712f1acf5b99d83
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260119"
---
# <a name="name-name-is-not-declared"></a><span data-ttu-id="ddc9c-102">Nome de '\<nome >' não está declarado</span><span class="sxs-lookup"><span data-stu-id="ddc9c-102">Name '\<name>' is not declared</span></span>
<span data-ttu-id="ddc9c-103">Uma declaração se refere a um elemento de programação, mas o compilador não pode localizar um elemento com esse nome exato.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-103">A statement refers to a programming element, but the compiler cannot find an element with that exact name.</span></span>  
  
 <span data-ttu-id="ddc9c-104">**ID do erro:** BC30451</span><span class="sxs-lookup"><span data-stu-id="ddc9c-104">**Error ID:** BC30451</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ddc9c-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="ddc9c-105">To correct this error</span></span>  
  
1. <span data-ttu-id="ddc9c-106">Verifique a ortografia do nome na declaração de referência.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-106">Check the spelling of the name in the referring statement.</span></span> <span data-ttu-id="ddc9c-107">Visual Basic diferencia maiusculas de minúsculas, mas qualquer outra variação de grafia é considerada como um nome completamente diferente.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-107">Visual Basic is case-insensitive, but any other variation in the spelling is regarded as a completely different name.</span></span> <span data-ttu-id="ddc9c-108">Observe que o caractere de sublinhado (`_`) é parte do nome e, portanto, parte da ortografia.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-108">Note that the underscore (`_`) is part of the name and therefore part of the spelling.</span></span>  
  
2. <span data-ttu-id="ddc9c-109">Verifique se você tem o operador de acesso de membro (`.`) entre um objeto e seus membros.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-109">Check that you have the member access operator (`.`) between an object and its member.</span></span> <span data-ttu-id="ddc9c-110">Por exemplo, se você tiver um <xref:System.Windows.Forms.TextBox> controle chamado `TextBox1`, para acessar seus <xref:System.Windows.Forms.TextBoxBase.Text%2A> propriedade, você deve digitar `TextBox1.Text`.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-110">For example, if you have a <xref:System.Windows.Forms.TextBox> control named `TextBox1`, to access its <xref:System.Windows.Forms.TextBoxBase.Text%2A> property you should type `TextBox1.Text`.</span></span> <span data-ttu-id="ddc9c-111">Se, em vez disso, você digita `TextBox1Text`, você criou um nome diferente.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-111">If instead you type `TextBox1Text`, you have created a different name.</span></span>  
  
3. <span data-ttu-id="ddc9c-112">Se a ortografia está correta e a sintaxe de qualquer acesso de membro de objeto está correta, verifique se que o elemento foi declarado.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-112">If the spelling is correct and the syntax of any object member access is correct, verify that the element has been declared.</span></span> <span data-ttu-id="ddc9c-113">Para obter mais informações, consulte [elementos declarados](../../programming-guide/language-features/declared-elements/index.md).</span><span class="sxs-lookup"><span data-stu-id="ddc9c-113">For more information, see [Declared Elements](../../programming-guide/language-features/declared-elements/index.md).</span></span>  
  
4. <span data-ttu-id="ddc9c-114">Se o elemento de programação tiver sido declarado, verifique se ele está no escopo.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-114">If the programming element has been declared, check that it is in scope.</span></span> <span data-ttu-id="ddc9c-115">Se a referência está fora da região que declara o elemento de programação, você precisa qualificar o nome do elemento.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-115">If the referring statement is outside the region declaring the programming element, you might need to qualify the element name.</span></span> <span data-ttu-id="ddc9c-116">Para obter mais informações, consulte [escopo no Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="ddc9c-116">For more information, see [Scope in Visual Basic](../../programming-guide/language-features/declared-elements/scope.md).</span></span>  

5. <span data-ttu-id="ddc9c-117">Se você não estiver usando um tipo totalmente qualificado ou o nome de tipo e membro (por exemplo, seu código fizer referência a uma propriedade como `MethodInfo.Name` em vez de `System.Reflection.MethodInfo.Name`), adicione um [instrução Imports](../statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="ddc9c-117">If you are not using a fully qualified type or type and member name (for example, your code refers to a property as `MethodInfo.Name` instead of `System.Reflection.MethodInfo.Name`), add an [Imports statement](../statements/imports-statement-net-namespace-and-type.md).</span></span>

6. <span data-ttu-id="ddc9c-118">Se você está tentando compilar um projeto de estilo do SDK (um projeto com um \*arquivo. vbproj que começa com a linha `<Project Sdk="Microsoft.NET.Sdk">`) e a mensagem de erro se refere a um tipo ou membro no assembly VisualBasic, configurar seu aplicativo para Compile com uma referência à biblioteca de tempo de execução do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-118">If you are attempting to compile an SDK-style project (a project with a \*.vbproj file that begins with the line `<Project Sdk="Microsoft.NET.Sdk">`), and the error message refers to a type or member in the Microsoft.VisualBasic.dll assembly, configure your application to compile with a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="ddc9c-119">Por padrão, um subconjunto da biblioteca é inserido em seu assembly em um projeto de estilo do SDK.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-119">By default, a subset of the library is embedded in your assembly in an SDK-style project.</span></span>

   <span data-ttu-id="ddc9c-120">Por exemplo, o exemplo a seguir falhará ao ser compilado porque o <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A?displayProperty=fullName> método não pode ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-120">For example, the following example fails to compile because the <xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A?displayProperty=fullName> method cannot be found.</span></span> <span data-ttu-id="ddc9c-121">Ele não será inserido no subconjunto do Runtime do Visual Basic, incluído com o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-121">It is not embedded in the subset of the Visual Basic Runtime included with your application.</span></span>  

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/program1.vb)]

   <span data-ttu-id="ddc9c-122">Para resolver esse erro, adicione a `<VBRuntime>Default</VBRuntime>` elemento aos projetos `<PropertyGroup>` seção, como a seguir de arquivo de projeto do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ddc9c-122">To address this error, add the `<VBRuntime>Default</VBRuntime>` element to the projects `<PropertyGroup>` section, as the following Visual Basic project file shows.</span></span>

   [!code-vb[BC30451](~/samples/snippets/visualbasic/language-reference/error-messages/bc30451/vbruntime.vbproj?highlight=6)]

## <a name="see-also"></a><span data-ttu-id="ddc9c-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ddc9c-123">See also</span></span>

- [<span data-ttu-id="ddc9c-124">Resumo de Declarações e Constantes</span><span class="sxs-lookup"><span data-stu-id="ddc9c-124">Declarations and Constants Summary</span></span>](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)
- [<span data-ttu-id="ddc9c-125">Convenções de nomenclatura do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ddc9c-125">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [<span data-ttu-id="ddc9c-126">Nomes de Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="ddc9c-126">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="ddc9c-127">Referências a Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="ddc9c-127">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
