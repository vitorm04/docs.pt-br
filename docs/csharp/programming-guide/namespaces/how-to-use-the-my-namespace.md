---
title: Como usar o guia de programação meu namespace-C#
description: Saiba como usar o namespace ' My '. O namespace ' My ' fornece acesso fácil e intuitivo a várias classes .NET.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, My namespace access
ms.assetid: e7152414-0ea5-4c8e-bf02-c8d5bbe45ff4
ms.openlocfilehash: 7abd5049a979d5a15d123052cba0cfdb35bf3fb7
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381704"
---
# <a name="how-to-use-the-my-namespace-c-programming-guide"></a><span data-ttu-id="fb04e-104">Como usar o namespace My (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="fb04e-104">How to use the My namespace (C# Programming Guide)</span></span>

<span data-ttu-id="fb04e-105">O <xref:Microsoft.VisualBasic.MyServices> namespace ( `My` em Visual Basic) fornece acesso fácil e intuitivo a várias classes .net, permitindo que você escreva código que interaja com o computador, o aplicativo, as configurações, os recursos e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="fb04e-105">The <xref:Microsoft.VisualBasic.MyServices> namespace (`My` in Visual Basic) provides easy and intuitive access to a number of .NET classes, enabling you to write code that interacts with the computer, application, settings, resources, and so on.</span></span> <span data-ttu-id="fb04e-106">Embora tenha sido projetado originalmente para ser usado com o Visual Basic, o namespace `MyServices` pode ser usado em aplicativos C#.</span><span class="sxs-lookup"><span data-stu-id="fb04e-106">Although originally designed for use with Visual Basic, the `MyServices` namespace can be used in C# applications.</span></span>  
  
 <span data-ttu-id="fb04e-107">Para obter mais informações sobre como usar o namespace `MyServices` no Visual Basic, consulte [Desenvolvimento com My](../../../visual-basic/developing-apps/development-with-my/index.md).</span><span class="sxs-lookup"><span data-stu-id="fb04e-107">For more information about using the `MyServices` namespace from Visual Basic, see [Development with My](../../../visual-basic/developing-apps/development-with-my/index.md).</span></span>  
  
## <a name="add-a-reference"></a><span data-ttu-id="fb04e-108">Adicionar uma referência</span><span class="sxs-lookup"><span data-stu-id="fb04e-108">Add a reference</span></span>

 <span data-ttu-id="fb04e-109">Antes de usar as classes `MyServices` em sua solução, é necessário adicionar uma referência à biblioteca do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fb04e-109">Before you can use the `MyServices` classes in your solution, you must add a reference to the Visual Basic library.</span></span>  
  
### <a name="add-a-reference-to-the-visual-basic-library"></a><span data-ttu-id="fb04e-110">Adicionar uma referência à biblioteca de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb04e-110">Add a reference to the Visual Basic library</span></span>  
  
1. <span data-ttu-id="fb04e-111">In **Gerenciador de Soluções**, clique com o botão direito do mouse no nó **Referências** e selecione **Adicionar Referência**.</span><span class="sxs-lookup"><span data-stu-id="fb04e-111">In **Solution Explorer**, right-click the **References** node, and select **Add Reference**.</span></span>  
  
2. <span data-ttu-id="fb04e-112">Quando a caixa de diálogo **Referências** for exibida, role a lista para baixo e selecione Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="fb04e-112">When the **References** dialog box appears, scroll down the list, and select Microsoft.VisualBasic.dll.</span></span>  
  
     <span data-ttu-id="fb04e-113">Também é possível incluir a seguinte linha na seção `using` na inicialização do seu programa.</span><span class="sxs-lookup"><span data-stu-id="fb04e-113">You might also want to include the following line in the `using` section at the start of your program.</span></span>  
  
     [!code-csharp[csProgGuideNamespaces#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#18)]  
  
## <a name="example"></a><span data-ttu-id="fb04e-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fb04e-114">Example</span></span>  
 <span data-ttu-id="fb04e-115">Este exemplo chama vários métodos estáticos contidos no namespace `MyServices`.</span><span class="sxs-lookup"><span data-stu-id="fb04e-115">This example calls various static methods contained in the `MyServices` namespace.</span></span> <span data-ttu-id="fb04e-116">Para que esse código seja compilado, deve ser adicionada uma referência ao Microsoft.VisualBasic.DLL ao projeto.</span><span class="sxs-lookup"><span data-stu-id="fb04e-116">For this code to compile, a reference to Microsoft.VisualBasic.DLL must be added to the project.</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#19)]  
  
 <span data-ttu-id="fb04e-117">Nem todas as classes no namespace `MyServices` podem ser chamadas em um aplicativo C#: por exemplo, a classe <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> não é compatível.</span><span class="sxs-lookup"><span data-stu-id="fb04e-117">Not all the classes in the `MyServices` namespace can be called from a C# application: for example, the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy> class is not compatible.</span></span> <span data-ttu-id="fb04e-118">Em vez disso, nesse caso específico, podem ser usados os métodos estáticos que fazem parte da <xref:Microsoft.VisualBasic.FileIO.FileSystem>, que também estão contidos na VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="fb04e-118">In this particular case, the static methods that are part of <xref:Microsoft.VisualBasic.FileIO.FileSystem>, which are also contained in VisualBasic.dll, can be used instead.</span></span> <span data-ttu-id="fb04e-119">Por exemplo, veja como usar um desses métodos para duplicar um diretório:</span><span class="sxs-lookup"><span data-stu-id="fb04e-119">For example, here is how to use one such method to duplicate a directory:</span></span>  
  
 [!code-csharp[csProgGuideNamespaces#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideNamespaces/CS/Namespaces3.cs#20)]  
  
## <a name="see-also"></a><span data-ttu-id="fb04e-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="fb04e-120">See also</span></span>

- [<span data-ttu-id="fb04e-121">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="fb04e-121">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fb04e-122">Namespaces</span><span class="sxs-lookup"><span data-stu-id="fb04e-122">Namespaces</span></span>](./index.md)
- [<span data-ttu-id="fb04e-123">Usando namespaces</span><span class="sxs-lookup"><span data-stu-id="fb04e-123">Using Namespaces</span></span>](./using-namespaces.md)
