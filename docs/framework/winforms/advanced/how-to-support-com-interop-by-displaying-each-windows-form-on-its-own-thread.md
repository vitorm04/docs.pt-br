---
title: Como dar suporte à interoperabilidade COM exibindo cada formulário do Windows Forms em um thread separado
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
ms.openlocfilehash: d0d8dfd4a19b31be790d2643847396d136098278
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085602"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a><span data-ttu-id="37d41-102">Como dar suporte à interoperabilidade COM exibindo cada formulário do Windows Forms em um thread separado</span><span class="sxs-lookup"><span data-stu-id="37d41-102">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>
<span data-ttu-id="37d41-103">Você pode resolver problemas de interoperabilidade com exibindo seu formulário em um [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] loop de mensagem, você pode criar usando o <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="37d41-103">You can resolve COM interoperability problems by displaying your form on a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] message loop, which you can create by using the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="37d41-104">Para fazer um Windows Form funcionar corretamente em um aplicativo cliente COM, execute o formulário em um loop de mensagem dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="37d41-104">To make a Windows Form work correctly from a COM client application, you must run the form on a Windows Forms message loop.</span></span> <span data-ttu-id="37d41-105">Para fazer isso, use uma das abordagens a seguir:</span><span class="sxs-lookup"><span data-stu-id="37d41-105">To do this, use one of the following approaches:</span></span>  
  
-   <span data-ttu-id="37d41-106">Use o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método para exibir o formulário do Windows.</span><span class="sxs-lookup"><span data-stu-id="37d41-106">Use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the Windows Form.</span></span> <span data-ttu-id="37d41-107">Para mais informações, consulte [Como dar suporte à interoperabilidade COM exibindo um Formulário do Windows Forms com o método ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="37d41-107">For more information, see [How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).</span></span>  
  
-   <span data-ttu-id="37d41-108">Exiba cada Windows Form em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="37d41-108">Display each Windows Form on a separate thread.</span></span>  
  
 <span data-ttu-id="37d41-109">Há suporte abrangente para este recurso no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="37d41-109">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="37d41-110">Consulte também [Instruções passo a passo: dando suporte à interoperabilidade COM exibindo cada Windows Form no próprio thread](https://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="37d41-110">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](https://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="37d41-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="37d41-111">Example</span></span>  
 <span data-ttu-id="37d41-112">O exemplo de código a seguir demonstra como exibir o formulário em um thread separado e chamar o <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> método para iniciar uma bomba de mensagem do Windows Forms nesse thread.</span><span class="sxs-lookup"><span data-stu-id="37d41-112">The following code example demonstrates how to display the form on a separate thread and call the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method to start a Windows Forms message pump on that thread.</span></span> <span data-ttu-id="37d41-113">Para usar essa abordagem, você deve empacotar as chamadas para o formulário do aplicativo não gerenciado usando o <xref:System.Windows.Forms.Control.Invoke%2A> método.</span><span class="sxs-lookup"><span data-stu-id="37d41-113">To use this approach, you must marshal any calls to the form from the unmanaged application by using the <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span>  
  
 <span data-ttu-id="37d41-114">Essa abordagem requer que cada instância de um formulário seja executada em seu próprio thread usando seu próprio loop de mensagem.</span><span class="sxs-lookup"><span data-stu-id="37d41-114">This approach requires that each instance of a form runs on its own thread by using its own message loop.</span></span> <span data-ttu-id="37d41-115">Não é possível ter mais de um loop de mensagem em execução por thread.</span><span class="sxs-lookup"><span data-stu-id="37d41-115">You cannot have more than one message loop running per thread.</span></span> <span data-ttu-id="37d41-116">Portanto, não é possível alterar o loop de mensagem do aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="37d41-116">Therefore, you cannot change the client application's message loop.</span></span> <span data-ttu-id="37d41-117">No entanto, é possível modificar o componente [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para iniciar um novo thread que usa seu próprio loop de mensagem.</span><span class="sxs-lookup"><span data-stu-id="37d41-117">However, you can modify the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] component to start a new thread that uses its own message loop.</span></span>  
  
 [!code-vb[System.Windows.Forms.ComInterop#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="37d41-118">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="37d41-118">Compiling the Code</span></span>  
  
-   <span data-ttu-id="37d41-119">Compile os tipos `COMForm`, `Form1` e `FormManager` em um assembly chamado `COMWinform.dll`.</span><span class="sxs-lookup"><span data-stu-id="37d41-119">Compile the `COMForm`, `Form1`, and `FormManager` types into an assembly called `COMWinform.dll`.</span></span> <span data-ttu-id="37d41-120">Registre o assembly de interoperabilidade COM usando um dos métodos descritos em [Empacotando um assembly para COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="37d41-120">Register the assembly for COM interop by using one of the methods described in [Packaging an Assembly for COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span></span> <span data-ttu-id="37d41-121">Agora você pode usar o assembly e o arquivo de biblioteca de tipos (.tlb) correspondente em aplicativos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="37d41-121">You can now use the assembly and its corresponding type library (.tlb) file in unmanaged applications.</span></span> <span data-ttu-id="37d41-122">Por exemplo, você pode usar a biblioteca de tipos como uma referência em um projeto executável do Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="37d41-122">For example, you can use the type library as a reference in a Visual Basic 6.0 executable project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37d41-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37d41-123">See Also</span></span>  
 [<span data-ttu-id="37d41-124">Expondo componentes do .NET Framework ao COM</span><span class="sxs-lookup"><span data-stu-id="37d41-124">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="37d41-125">Empacotando um assembly para COM</span><span class="sxs-lookup"><span data-stu-id="37d41-125">Packaging an Assembly for COM</span></span>](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [<span data-ttu-id="37d41-126">Registrando assemblies usando COM</span><span class="sxs-lookup"><span data-stu-id="37d41-126">Registering Assemblies with COM</span></span>](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [<span data-ttu-id="37d41-127">Como dar suporte à interoperabilidade COM exibindo um Windows Form com o método ShowDialog</span><span class="sxs-lookup"><span data-stu-id="37d41-127">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [<span data-ttu-id="37d41-128">Visão Geral dos Aplicativos dos Windows Forms e Aplicativos Não Gerenciados</span><span class="sxs-lookup"><span data-stu-id="37d41-128">Windows Forms and Unmanaged Applications Overview</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)
