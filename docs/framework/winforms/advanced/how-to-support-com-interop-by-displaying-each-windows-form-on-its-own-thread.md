---
title: 'Como: dar suporte à interoperabilidade COM exibindo cada formulário do Windows Forms em um thread separado'
ms.date: 03/30/2017
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
ms.openlocfilehash: 90bbd7df45424f8513598e9d7439d8ae6bf6f52c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040306"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a><span data-ttu-id="773d9-102">Como: Suporte à interoperabilidade COM exibindo cada formulário do Windows em seu próprio thread</span><span class="sxs-lookup"><span data-stu-id="773d9-102">How to: Support COM interop by displaying each Windows Form on its own thread</span></span>

<span data-ttu-id="773d9-103">Você pode resolver problemas de interoperabilidade com exibindo seu formulário em um .NET Framework loop de mensagem, que pode ser criado <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> usando o método.</span><span class="sxs-lookup"><span data-stu-id="773d9-103">You can resolve COM interoperability problems by displaying your form on a .NET Framework message loop, which you can create by using the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="773d9-104">Para fazer um Windows Form funcionar corretamente em um aplicativo cliente COM, execute o formulário em um loop de mensagem dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="773d9-104">To make a Windows Form work correctly from a COM client application, you must run the form on a Windows Forms message loop.</span></span> <span data-ttu-id="773d9-105">Para fazer isso, use uma das abordagens a seguir:</span><span class="sxs-lookup"><span data-stu-id="773d9-105">To do this, use one of the following approaches:</span></span>

- <span data-ttu-id="773d9-106">Use o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método para exibir o formulário do Windows.</span><span class="sxs-lookup"><span data-stu-id="773d9-106">Use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to display the Windows Form.</span></span> <span data-ttu-id="773d9-107">Para obter mais informações, confira [Como: Suporte à interoperabilidade COM exibindo um formulário do Windows](com-interop-by-displaying-a-windows-form-shadow.md)com o método ShowDialog.</span><span class="sxs-lookup"><span data-stu-id="773d9-107">For more information, see [How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method](com-interop-by-displaying-a-windows-form-shadow.md).</span></span>

- <span data-ttu-id="773d9-108">Exiba cada Windows Form em um thread separado.</span><span class="sxs-lookup"><span data-stu-id="773d9-108">Display each Windows Form on a separate thread.</span></span>

<span data-ttu-id="773d9-109">Há amplo suporte para esse recurso no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="773d9-109">There is extensive support for this feature in Visual Studio.</span></span>

<span data-ttu-id="773d9-110">Consulte [também o passo a passos: Suporte à interoperabilidade COM exibindo cada formulário do Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100))em seu próprio thread.</span><span class="sxs-lookup"><span data-stu-id="773d9-110">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).</span></span>

## <a name="example"></a><span data-ttu-id="773d9-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="773d9-111">Example</span></span>

<span data-ttu-id="773d9-112">O exemplo de código a seguir demonstra como exibir o formulário em um thread separado e chamar <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> o método para iniciar um Windows Forms bomba de mensagem nesse thread.</span><span class="sxs-lookup"><span data-stu-id="773d9-112">The following code example demonstrates how to display the form on a separate thread and call the <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> method to start a Windows Forms message pump on that thread.</span></span> <span data-ttu-id="773d9-113">Para usar essa abordagem, você deve realizar marshaling de todas as chamadas para o formulário a partir do aplicativo não <xref:System.Windows.Forms.Control.Invoke%2A> gerenciado usando o método.</span><span class="sxs-lookup"><span data-stu-id="773d9-113">To use this approach, you must marshal any calls to the form from the unmanaged application by using the <xref:System.Windows.Forms.Control.Invoke%2A> method.</span></span>

<span data-ttu-id="773d9-114">Essa abordagem requer que cada instância de um formulário seja executada em seu próprio thread usando seu próprio loop de mensagem.</span><span class="sxs-lookup"><span data-stu-id="773d9-114">This approach requires that each instance of a form runs on its own thread by using its own message loop.</span></span> <span data-ttu-id="773d9-115">Não é possível ter mais de um loop de mensagem em execução por thread.</span><span class="sxs-lookup"><span data-stu-id="773d9-115">You cannot have more than one message loop running per thread.</span></span> <span data-ttu-id="773d9-116">Portanto, não é possível alterar o loop de mensagem do aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="773d9-116">Therefore, you cannot change the client application's message loop.</span></span> <span data-ttu-id="773d9-117">No entanto, você pode modificar o componente .NET Framework para iniciar um novo thread que usa seu próprio loop de mensagem.</span><span class="sxs-lookup"><span data-stu-id="773d9-117">However, you can modify the .NET Framework component to start a new thread that uses its own message loop.</span></span>

[!code-vb[System.Windows.Forms.ComInterop#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]

[!code-vb[System.Windows.Forms.ComInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]

[!code-vb[System.Windows.Forms.ComInterop#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]

## <a name="compile-the-code"></a><span data-ttu-id="773d9-118">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="773d9-118">Compile the code</span></span>

<span data-ttu-id="773d9-119">Compile os tipos `COMForm`, `Form1` e `FormManager` em um assembly chamado `COMWinform.dll`.</span><span class="sxs-lookup"><span data-stu-id="773d9-119">Compile the `COMForm`, `Form1`, and `FormManager` types into an assembly called `COMWinform.dll`.</span></span> <span data-ttu-id="773d9-120">Registre o assembly de interoperabilidade COM usando um dos métodos descritos em [Empacotando um assembly para COM](../../interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="773d9-120">Register the assembly for COM interop by using one of the methods described in [Packaging an Assembly for COM](../../interop/packaging-an-assembly-for-com.md).</span></span> <span data-ttu-id="773d9-121">Agora você pode usar o assembly e o arquivo de biblioteca de tipos (.tlb) correspondente em aplicativos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="773d9-121">You can now use the assembly and its corresponding type library (.tlb) file in unmanaged applications.</span></span> <span data-ttu-id="773d9-122">Por exemplo, você pode usar a biblioteca de tipos como uma referência em um projeto executável do Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="773d9-122">For example, you can use the type library as a reference in a Visual Basic 6.0 executable project.</span></span>

## <a name="see-also"></a><span data-ttu-id="773d9-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="773d9-123">See also</span></span>

- [<span data-ttu-id="773d9-124">Expondo componentes do .NET Framework ao COM</span><span class="sxs-lookup"><span data-stu-id="773d9-124">Exposing .NET Framework Components to COM</span></span>](../../interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="773d9-125">Empacotando um assembly para COM</span><span class="sxs-lookup"><span data-stu-id="773d9-125">Packaging an Assembly for COM</span></span>](../../interop/packaging-an-assembly-for-com.md)
- [<span data-ttu-id="773d9-126">Registrando assemblies usando COM</span><span class="sxs-lookup"><span data-stu-id="773d9-126">Registering Assemblies with COM</span></span>](../../interop/registering-assemblies-with-com.md)
- [<span data-ttu-id="773d9-127">Como: Suporte à interoperabilidade COM exibindo um formulário do Windows com o método ShowDialog</span><span class="sxs-lookup"><span data-stu-id="773d9-127">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](com-interop-by-displaying-a-windows-form-shadow.md)
- [<span data-ttu-id="773d9-128">Visão Geral dos Aplicativos dos Windows Forms e Aplicativos Não Gerenciados</span><span class="sxs-lookup"><span data-stu-id="773d9-128">Windows Forms and Unmanaged Applications Overview</span></span>](windows-forms-and-unmanaged-applications-overview.md)
