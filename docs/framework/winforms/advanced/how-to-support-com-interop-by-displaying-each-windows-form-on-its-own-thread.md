---
title: 'Como: Dar suporte à interoperabilidade com exibindo cada formulário do Windows em seu próprio Thread'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
ms.openlocfilehash: 91c0b6384d8c39848cfd199950034d2f62e716df
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441743"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a><span data-ttu-id="429bf-102">Como: Dar suporte à interoperabilidade com exibindo cada formulário do Windows em seu próprio Thread</span><span class="sxs-lookup"><span data-stu-id="429bf-102">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>
<span data-ttu-id="429bf-103">Você pode resolver problemas de interoperabilidade com exibindo seu formulário em um [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] loop de mensagem, você pode criar usando o <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="429bf-103">You can resolve COM interoperability problems by displaying your form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop, which you can create by using the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="429bf-104">Para fazer um Windows Form funcionar corretamente em um aplicativo cliente COM, execute o formulário em um loop de mensagem dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="429bf-104">To make a Windows Form work correctly from a COM client application, you must run the form on a Windows Forms message loop.</span></span> <span data-ttu-id="429bf-105">Para fazer isso, use uma das abordagens a seguir:</span><span class="sxs-lookup"><span data-stu-id="429bf-105">To do this, use one of the following approaches:</span></span>  
  
-   <span data-ttu-id="429bf-106">Use o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método para exibir o formulário do Windows.</span><span class="sxs-lookup"><span data-stu-id="429bf-106">Use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the Windows Form.</span></span> <span data-ttu-id="429bf-107">Para obter mais informações, confira [Como: Dar suporte à interoperabilidade com exibindo um formulário do Windows com o método ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="429bf-107">For more information, see [How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).</span></span>  
  
-   <span data-ttu-id="429bf-108">Exiba cada Windows Form em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="429bf-108">Display each Windows Form on a separate thread.</span></span>  
  
 <span data-ttu-id="429bf-109">Há suporte abrangente para este recurso no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="429bf-109">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="429bf-110">Consulte também [passo a passo: Dando suporte à interoperabilidade com exibindo cada formulário do Windows em seu próprio Thread](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="429bf-110">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="429bf-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="429bf-111">Example</span></span>  
 <span data-ttu-id="429bf-112">O exemplo de código a seguir demonstra como exibir o formulário em um thread separado e chamar o <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> método para iniciar uma bomba de mensagem do Windows Forms nesse thread.</span><span class="sxs-lookup"><span data-stu-id="429bf-112">The following code example demonstrates how to display the form on a separate thread and call the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method to start a Windows Forms message pump on that thread.</span></span> <span data-ttu-id="429bf-113">Para usar essa abordagem, você deve empacotar as chamadas para o formulário do aplicativo não gerenciado usando o <xref:System.Windows.Forms.Control.Invoke%2A> método.</span><span class="sxs-lookup"><span data-stu-id="429bf-113">To use this approach, you must marshal any calls to the form from the unmanaged application by using the <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span>  
  
 <span data-ttu-id="429bf-114">Essa abordagem requer que cada instância de um formulário seja executada em seu próprio thread usando seu próprio loop de mensagem.</span><span class="sxs-lookup"><span data-stu-id="429bf-114">This approach requires that each instance of a form runs on its own thread by using its own message loop.</span></span> <span data-ttu-id="429bf-115">Não é possível ter mais de um loop de mensagem em execução por thread.</span><span class="sxs-lookup"><span data-stu-id="429bf-115">You cannot have more than one message loop running per thread.</span></span> <span data-ttu-id="429bf-116">Portanto, não é possível alterar o loop de mensagem do aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="429bf-116">Therefore, you cannot change the client application's message loop.</span></span> <span data-ttu-id="429bf-117">No entanto, é possível modificar o componente [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para iniciar um novo thread que usa seu próprio loop de mensagem.</span><span class="sxs-lookup"><span data-stu-id="429bf-117">However, you can modify the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] component to start a new thread that uses its own message loop.</span></span>  
  
 [!code-vb[System.Windows.Forms.ComInterop#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="429bf-118">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="429bf-118">Compiling the Code</span></span>  
  
-   <span data-ttu-id="429bf-119">Compile os tipos `COMForm`, `Form1` e `FormManager` em um assembly chamado `COMWinform.dll`.</span><span class="sxs-lookup"><span data-stu-id="429bf-119">Compile the `COMForm`, `Form1`, and `FormManager` types into an assembly called `COMWinform.dll`.</span></span> <span data-ttu-id="429bf-120">Registre o assembly de interoperabilidade COM usando um dos métodos descritos em [Empacotando um assembly para COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="429bf-120">Register the assembly for COM interop by using one of the methods described in [Packaging an Assembly for COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span></span> <span data-ttu-id="429bf-121">Agora você pode usar o assembly e o arquivo de biblioteca de tipos (.tlb) correspondente em aplicativos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="429bf-121">You can now use the assembly and its corresponding type library (.tlb) file in unmanaged applications.</span></span> <span data-ttu-id="429bf-122">Por exemplo, você pode usar a biblioteca de tipos como uma referência em um projeto executável do Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="429bf-122">For example, you can use the type library as a reference in a Visual Basic 6.0 executable project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="429bf-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="429bf-123">See also</span></span>
- [<span data-ttu-id="429bf-124">Expondo componentes do .NET Framework ao COM</span><span class="sxs-lookup"><span data-stu-id="429bf-124">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="429bf-125">Empacotando um assembly para COM</span><span class="sxs-lookup"><span data-stu-id="429bf-125">Packaging an Assembly for COM</span></span>](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)
- [<span data-ttu-id="429bf-126">Registrando assemblies usando COM</span><span class="sxs-lookup"><span data-stu-id="429bf-126">Registering Assemblies with COM</span></span>](../../../../docs/framework/interop/registering-assemblies-with-com.md)
- [<span data-ttu-id="429bf-127">Como: Dar suporte à interoperabilidade com exibindo um formulário do Windows com o método ShowDialog</span><span class="sxs-lookup"><span data-stu-id="429bf-127">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)
- [<span data-ttu-id="429bf-128">Visão Geral dos Aplicativos dos Windows Forms e Aplicativos Não Gerenciados</span><span class="sxs-lookup"><span data-stu-id="429bf-128">Windows Forms and Unmanaged Applications Overview</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)
