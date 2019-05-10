---
title: 'Passo a passo: hospedar um relógio do WPF no Win32'
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 4001c34f6673e036bdbf731baed782c6dc0a16b0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64755908"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a><span data-ttu-id="ed68f-102">Passo a passo: hospedar um relógio do WPF no Win32</span><span class="sxs-lookup"><span data-stu-id="ed68f-102">Walkthrough: Hosting a WPF Clock in Win32</span></span>

<span data-ttu-id="ed68f-103">Para colocar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dentro de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplicativos, usam <xref:System.Windows.Interop.HwndSource>, que fornece o HWND que contém seu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo.</span><span class="sxs-lookup"><span data-stu-id="ed68f-103">To put [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] applications, use <xref:System.Windows.Interop.HwndSource>, which provides the HWND that contains your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="ed68f-104">Primeiro, você cria o <xref:System.Windows.Interop.HwndSource>, dando a ele parâmetros semelhantes a CreateWindow.</span><span class="sxs-lookup"><span data-stu-id="ed68f-104">First you create the <xref:System.Windows.Interop.HwndSource>, giving it parameters similar to CreateWindow.</span></span> <span data-ttu-id="ed68f-105">Em seguida, você informa o <xref:System.Windows.Interop.HwndSource> sobre o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] conteúdo que você deseja dentro dele.</span><span class="sxs-lookup"><span data-stu-id="ed68f-105">Then you tell the <xref:System.Windows.Interop.HwndSource> about the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content you want inside it.</span></span> <span data-ttu-id="ed68f-106">Finalmente, você obtém o HWND do <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="ed68f-106">Finally, you get the HWND out of the <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="ed68f-107">Este passo a passo ilustra como criar um misto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dentro de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplicativo que reimplementa o sistema operacional **Date and Time Properties** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="ed68f-107">This walkthrough illustrates how to create a mixed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application that reimplements the operating system **Date and Time Properties** dialog.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ed68f-108">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="ed68f-108">Prerequisites</span></span>

<span data-ttu-id="ed68f-109">Consulte [Interoperação Win32 e WPF](wpf-and-win32-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="ed68f-109">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="how-to-use-this-tutorial"></a><span data-ttu-id="ed68f-110">Como usar esse tutorial</span><span class="sxs-lookup"><span data-stu-id="ed68f-110">How to Use This Tutorial</span></span>

<span data-ttu-id="ed68f-111">Este tutorial mostra as etapas importantes de produção de um aplicativo de interoperação.</span><span class="sxs-lookup"><span data-stu-id="ed68f-111">This tutorial concentrates on the important steps of producing an interoperation application.</span></span> <span data-ttu-id="ed68f-112">O tutorial é feito por uma amostra [exemplo de interoperação de relógio do Win32](https://go.microsoft.com/fwlink/?LinkID=160051), mas esse exemplo é reflete o produto final.</span><span class="sxs-lookup"><span data-stu-id="ed68f-112">The tutorial is backed by a sample, [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051), but that sample is reflective of the end product.</span></span> <span data-ttu-id="ed68f-113">Este tutorial documenta as etapas como se você estivesse iniciando com um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projeto de sua preferência, talvez um projeto pré-existente e você estivesse adicionando hospedado [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ed68f-113">This tutorial documents the steps as if you were starting with an existing [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project of your own, perhaps a pre-existing project, and you were adding a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to your application.</span></span> <span data-ttu-id="ed68f-114">Você pode comparar seu produto final com [exemplo de interoperação de relógio do Win32](https://go.microsoft.com/fwlink/?LinkID=160051).</span><span class="sxs-lookup"><span data-stu-id="ed68f-114">You can compare your end product with [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051).</span></span>

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a><span data-ttu-id="ed68f-115">Um passo a passo do Windows Presentation Framework no Win32 (HwndSource)</span><span class="sxs-lookup"><span data-stu-id="ed68f-115">A Walkthrough of Windows Presentation Framework Inside Win32 (HwndSource)</span></span>

<span data-ttu-id="ed68f-116">O gráfico a seguir mostra o produto final desejado deste tutorial:</span><span class="sxs-lookup"><span data-stu-id="ed68f-116">The following graphic shows the intended end product of this tutorial:</span></span>

![Captura de tela que mostra a caixa de diálogo Propriedades de data e hora.](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

<span data-ttu-id="ed68f-118">Você pode recriar esta caixa de diálogo com a criação de um C++ projeto do Win32 no Visual Studio e usando o editor de caixa de diálogo para criar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="ed68f-118">You can recreate this dialog by creating a C++ Win32 project in Visual Studio, and using the dialog editor to create the following:</span></span>

![Caixa de diálogo de propriedades de data e hora recriada](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

<span data-ttu-id="ed68f-120">(Não é necessário usar [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] usar <xref:System.Windows.Interop.HwndSource>, e você não precisará usar C++ para escrever [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programas, mas isso é uma maneira bastante comum de fazê-lo e funciona bem para uma explicação do tutorial em passos).</span><span class="sxs-lookup"><span data-stu-id="ed68f-120">(You do not need to use [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] to use <xref:System.Windows.Interop.HwndSource>, and you do not need to use C++ to write [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programs, but this is a fairly typical way to do it, and lends itself well to a stepwise tutorial explanation).</span></span>

<span data-ttu-id="ed68f-121">Você precisa realizar cinco subpassos para colocar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio na caixa de diálogo:</span><span class="sxs-lookup"><span data-stu-id="ed68f-121">You need to accomplish five particular substeps in order to put a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock into the dialog:</span></span>

1. <span data-ttu-id="ed68f-122">Habilitar seu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projeto para chamar código gerenciado (**/clr**) alterando as configurações de projeto no [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ed68f-122">Enable your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project to call managed code (**/clr**) by changing project settings in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].</span></span>

2. <span data-ttu-id="ed68f-123">Criar uma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> em uma DLL separada.</span><span class="sxs-lookup"><span data-stu-id="ed68f-123">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> in a separate DLL.</span></span>

3. <span data-ttu-id="ed68f-124">Colocar isso [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> dentro de um <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="ed68f-124">Put that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> inside an <xref:System.Windows.Interop.HwndSource>.</span></span>

4. <span data-ttu-id="ed68f-125">Obtenha um HWND para que <xref:System.Windows.Controls.Page> usando o <xref:System.Windows.Interop.HwndSource.Handle%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="ed68f-125">Get an HWND for that <xref:System.Windows.Controls.Page> using the <xref:System.Windows.Interop.HwndSource.Handle%2A> property.</span></span>

5. <span data-ttu-id="ed68f-126">Use [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] para decidir onde colocar a HWND dentro maior [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplicativo</span><span class="sxs-lookup"><span data-stu-id="ed68f-126">Use [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] to decide where to place the HWND within the larger [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application</span></span>

## <a name="clr"></a><span data-ttu-id="ed68f-127">/clr</span><span class="sxs-lookup"><span data-stu-id="ed68f-127">/clr</span></span>

<span data-ttu-id="ed68f-128">A primeira etapa é transformar esse unmanaged [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projeto em um que pode chamar o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ed68f-128">The first step is to turn this unmanaged [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project into one that can call managed code.</span></span> <span data-ttu-id="ed68f-129">Você usa a opção de compilador /clr, que vinculará as DLLs necessárias que você deseja usar e ajustará o método principal para uso com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ed68f-129">You use the /clr compiler option, which will link to the necessary DLLs you want to use, and adjust the Main method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>

<span data-ttu-id="ed68f-130">Para habilitar o uso de código gerenciado dentro do projeto C++: Clique com botão direito no projeto win32clock e selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="ed68f-130">To enable the use of managed code inside the C++ project: Right-click on win32clock project and select **Properties**.</span></span> <span data-ttu-id="ed68f-131">Sobre o **gerais** página de propriedades (o padrão), altere o suporte a Common Language Runtime para `/clr`.</span><span class="sxs-lookup"><span data-stu-id="ed68f-131">On the **General** property page (the default), change Common Language Runtime support to `/clr`.</span></span>

<span data-ttu-id="ed68f-132">Em seguida, adicionar referências às DLLs necessárias para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore, PresentationFramework. dll, System. dll, WindowsBase. dll, UIAutomationProvider. dll e UIAutomationTypes. dll.</span><span class="sxs-lookup"><span data-stu-id="ed68f-132">Next, add references to DLLs necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll, PresentationFramework.dll, System.dll, WindowsBase.dll, UIAutomationProvider.dll, and UIAutomationTypes.dll.</span></span> <span data-ttu-id="ed68f-133">(Seguir as instruções pressupõe que o sistema operacional está instalado na unidade C:.)</span><span class="sxs-lookup"><span data-stu-id="ed68f-133">(Following instructions assume the operating system is installed on C: drive.)</span></span>

1. <span data-ttu-id="ed68f-134">Clique em projeto win32clock e selecione **referências...** e dentro desse diálogo:</span><span class="sxs-lookup"><span data-stu-id="ed68f-134">Right-click win32clock project and select **References...**, and inside that dialog:</span></span>

2. <span data-ttu-id="ed68f-135">Clique em projeto win32clock e selecione **referências...** .</span><span class="sxs-lookup"><span data-stu-id="ed68f-135">Right-click win32clock project and select **References...**.</span></span>

3. <span data-ttu-id="ed68f-136">Clique em **adicionar nova referência**, clique na guia Procurar, digite C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll e clique em Okey.</span><span class="sxs-lookup"><span data-stu-id="ed68f-136">Click **Add New Reference**, click Browse tab, enter C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, and click OK.</span></span>

4. <span data-ttu-id="ed68f-137">Repita para PresentationFramework. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span><span class="sxs-lookup"><span data-stu-id="ed68f-137">Repeat for PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span></span>

5. <span data-ttu-id="ed68f-138">Repita para WindowsBase. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span><span class="sxs-lookup"><span data-stu-id="ed68f-138">Repeat for WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span></span>

6. <span data-ttu-id="ed68f-139">Repita para UIAutomationTypes. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span><span class="sxs-lookup"><span data-stu-id="ed68f-139">Repeat for UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span></span>

7. <span data-ttu-id="ed68f-140">Repita para UIAutomationProvider. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span><span class="sxs-lookup"><span data-stu-id="ed68f-140">Repeat for UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span></span>

8. <span data-ttu-id="ed68f-141">Clique em **adicionar nova referência**, selecione System. dll e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="ed68f-141">Click **Add New Reference**, select System.dll, and click **OK**.</span></span>

9. <span data-ttu-id="ed68f-142">Clique em **Okey** para as páginas de propriedades do win32clock para adicionar referências de saída.</span><span class="sxs-lookup"><span data-stu-id="ed68f-142">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>

 <span data-ttu-id="ed68f-143">Por fim, adicione a `STAThreadAttribute` para o `_tWinMain` método para uso com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="ed68f-143">Finally, add the `STAThreadAttribute` to the `_tWinMain` method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span></span>

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

<span data-ttu-id="ed68f-144">Esse atributo instrui o [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] que quando ele inicializa [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], ele deve usar um modelo de compartimento de único thread (STA), que é necessário para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="ed68f-144">This attribute tells the [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] that when it initializes [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], it should use a single threaded apartment model (STA), which is necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (and [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).</span></span>

## <a name="create-a-windows-presentation-framework-page"></a><span data-ttu-id="ed68f-145">Criar uma página do Windows Presentation Framework</span><span class="sxs-lookup"><span data-stu-id="ed68f-145">Create a Windows Presentation Framework Page</span></span>

<span data-ttu-id="ed68f-146">Em seguida, crie uma DLL que define uma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>.</span><span class="sxs-lookup"><span data-stu-id="ed68f-146">Next, you create a DLL that defines a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="ed68f-147">Geralmente é mais fácil criar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> como um aplicativo autônomo e a gravação e a depuração de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] parte dessa forma.</span><span class="sxs-lookup"><span data-stu-id="ed68f-147">It’s often easiest to create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> as a standalone application, and write and debug the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion that way.</span></span> <span data-ttu-id="ed68f-148">Depois disso, o que o projeto pode ser convertido em uma DLL clicando com o projeto, clicando em **propriedades**, indo para o aplicativo e alterar o tipo de saída para a biblioteca de classes do Windows.</span><span class="sxs-lookup"><span data-stu-id="ed68f-148">Once done, that project can be turned into a DLL by right-clicking the project, clicking on **Properties**, going to the Application, and changing Output type to Windows Class Library.</span></span>

<span data-ttu-id="ed68f-149">O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] projeto de dll, em seguida, pode ser combinado com o [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projeto (uma solução que contém dois projetos) – clique com o botão direito na solução, selecione **Adicionar\projeto**.</span><span class="sxs-lookup"><span data-stu-id="ed68f-149">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll project can then be combined with the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project (one solution that contains two projects) – right-click on the solution, select **Add\Existing Project**.</span></span>

<span data-ttu-id="ed68f-150">Para usá-la [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projeto, você precisa adicionar uma referência:</span><span class="sxs-lookup"><span data-stu-id="ed68f-150">To use that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll from the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project, you need to add a reference:</span></span>

1. <span data-ttu-id="ed68f-151">Clique em projeto win32clock e selecione **referências...** .</span><span class="sxs-lookup"><span data-stu-id="ed68f-151">Right-click win32clock project and select **References...**.</span></span>

2. <span data-ttu-id="ed68f-152">Clique em **adicionar nova referência**.</span><span class="sxs-lookup"><span data-stu-id="ed68f-152">Click **Add New Reference**.</span></span>

3. <span data-ttu-id="ed68f-153">Clique na guia **Projetos**. Selecione WPFClock, clique em OK.</span><span class="sxs-lookup"><span data-stu-id="ed68f-153">Click the **Projects** tab. Select WPFClock, click OK.</span></span>

4. <span data-ttu-id="ed68f-154">Clique em **Okey** para as páginas de propriedades do win32clock para adicionar referências de saída.</span><span class="sxs-lookup"><span data-stu-id="ed68f-154">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>

## <a name="hwndsource"></a><span data-ttu-id="ed68f-155">HwndSource</span><span class="sxs-lookup"><span data-stu-id="ed68f-155">HwndSource</span></span>

<span data-ttu-id="ed68f-156">Em seguida, use <xref:System.Windows.Interop.HwndSource> para fazer a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> se parecer com um HWND.</span><span class="sxs-lookup"><span data-stu-id="ed68f-156">Next, you use <xref:System.Windows.Interop.HwndSource> to make the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> look like an HWND.</span></span> <span data-ttu-id="ed68f-157">Você adiciona este bloco de código a um arquivo C++:</span><span class="sxs-lookup"><span data-stu-id="ed68f-157">You add this block of code to a C++ file:</span></span>

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;

    HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
        HwndSource^ source = gcnew HwndSource(
            0, // class style
            WS_VISIBLE | WS_CHILD, // style
            0, // exstyle
            x, y, width, height,
            "hi", // NAME
            IntPtr(parent)        // parent window
            );

        UIElement^ page = gcnew WPFClock::Clock();
        source->RootVisual = page;
        return (HWND) source->Handle.ToPointer();
    }
}
}
```

 <span data-ttu-id="ed68f-158">Esse é uma parte grande do código que poderia ser explicada.</span><span class="sxs-lookup"><span data-stu-id="ed68f-158">This is a long piece of code that could use some explanation.</span></span> <span data-ttu-id="ed68f-159">A primeira parte é composta por várias cláusulas para que você não precise qualificar totalmente todas as chamadas:</span><span class="sxs-lookup"><span data-stu-id="ed68f-159">The first part is various clauses so that you do not need to fully qualify all the calls:</span></span>

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;
```

 <span data-ttu-id="ed68f-160">Em seguida, você define uma função que cria o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de conteúdo, coloca um <xref:System.Windows.Interop.HwndSource> ao redor e retorna o HWND:</span><span class="sxs-lookup"><span data-stu-id="ed68f-160">Then you define a function that creates the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content, puts an <xref:System.Windows.Interop.HwndSource> around it, and returns the HWND:</span></span>

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

<span data-ttu-id="ed68f-161">Primeiro, você cria um <xref:System.Windows.Interop.HwndSource>, cujos parâmetros são semelhantes do CreateWindow:</span><span class="sxs-lookup"><span data-stu-id="ed68f-161">First you create an <xref:System.Windows.Interop.HwndSource>, whose parameters are similar to CreateWindow:</span></span>

```cpp
HwndSource^ source = gcnew HwndSource(
    0, // class style
    WS_VISIBLE | WS_CHILD, // style
    0, // exstyle
    x, y, width, height,
    "hi", // NAME
    IntPtr(parent) // parent window
);
```

<span data-ttu-id="ed68f-162">Em seguida, você cria o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] classe de conteúdo chamando seu construtor:</span><span class="sxs-lookup"><span data-stu-id="ed68f-162">Then you create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content class by calling its constructor:</span></span>

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

<span data-ttu-id="ed68f-163">Em seguida, conecte-se a página para o <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="ed68f-163">You then connect the page to the <xref:System.Windows.Interop.HwndSource>:</span></span>

```cpp
source->RootVisual = page;
```

 <span data-ttu-id="ed68f-164">E na linha final, retorne o HWND para o <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="ed68f-164">And in the final line, return the HWND for the <xref:System.Windows.Interop.HwndSource>:</span></span>

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a><span data-ttu-id="ed68f-165">Posicionamento do Hwnd</span><span class="sxs-lookup"><span data-stu-id="ed68f-165">Positioning the Hwnd</span></span>

<span data-ttu-id="ed68f-166">Agora que você tem um HWND que contém o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio, você precisará colocar esse HWND dentro de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="ed68f-166">Now that you have an HWND that contains the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you need to put that HWND inside the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog.</span></span> <span data-ttu-id="ed68f-167">Se você soubesse onde colocar a HWND, você apenas passaria tamanho e o local para o `GetHwnd` função que você definiu anteriormente.</span><span class="sxs-lookup"><span data-stu-id="ed68f-167">If you knew just where to put the HWND, you would just pass that size and location to the `GetHwnd` function you defined earlier.</span></span> <span data-ttu-id="ed68f-168">Mas você usou um arquivo de recurso para definir a caixa de diálogo, então não tem muita certeza sobre onde os HWNDs estão posicionados.</span><span class="sxs-lookup"><span data-stu-id="ed68f-168">But you used a resource file to define the dialog, so you are not exactly sure where any of the HWNDs are positioned.</span></span> <span data-ttu-id="ed68f-169">Você pode usar o [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] editor de caixa de diálogo para colocar uma [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] estático controlar onde você deseja que o relógio fique ("Inserir relógio aqui") e usá-lo para posicionar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio.</span><span class="sxs-lookup"><span data-stu-id="ed68f-169">You can use the [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] dialog editor to put a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] STATIC control where you want the clock to go ("Insert clock here"), and use that to position the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock.</span></span>

<span data-ttu-id="ed68f-170">Lidar com WM_INITDIALOG, você usa `GetDlgItem` para recuperar o HWND para o espaço reservado STATIC:</span><span class="sxs-lookup"><span data-stu-id="ed68f-170">Where you handle WM_INITDIALOG, you use `GetDlgItem` to retrieve the HWND for the placeholder STATIC:</span></span>

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

<span data-ttu-id="ed68f-171">Você, em seguida, calcula o tamanho e posição do espaço reservado STATIC, portanto, você pode colocar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio naquele local:</span><span class="sxs-lookup"><span data-stu-id="ed68f-171">You then calculate the size and position of that placeholder STATIC, so you can put the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock in that place:</span></span>

<span data-ttu-id="ed68f-172">Retângulo RECT;</span><span class="sxs-lookup"><span data-stu-id="ed68f-172">RECT rectangle;</span></span>

```cpp
GetWindowRect(placeholder, &rectangle);
int width = rectangle.right - rectangle.left;
int height = rectangle.bottom - rectangle.top;
POINT point;
point.x = rectangle.left;
point.y = rectangle.top;
result = MapWindowPoints(NULL, hDlg, &point, 1);
```

<span data-ttu-id="ed68f-173">Em seguida, oculte o espaço reservado STATIC:</span><span class="sxs-lookup"><span data-stu-id="ed68f-173">Then you hide the placeholder STATIC:</span></span>

```cpp
ShowWindow(placeholder, SW_HIDE);
```

<span data-ttu-id="ed68f-174">E crie o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio HWND neste local:</span><span class="sxs-lookup"><span data-stu-id="ed68f-174">And create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock HWND in that location:</span></span>

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

<span data-ttu-id="ed68f-175">Para tornar o tutorial interessante e produzir um real [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio, você precisará criar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] neste ponto de controle de relógio.</span><span class="sxs-lookup"><span data-stu-id="ed68f-175">To make the tutorial interesting, and to produce a real [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you will need to create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock control at this point.</span></span> <span data-ttu-id="ed68f-176">Você pode fazer isso basicamente na marcação, com apenas alguns manipuladores de eventos no code-behind.</span><span class="sxs-lookup"><span data-stu-id="ed68f-176">You can do so mostly in markup, with just a few event handlers in code-behind.</span></span> <span data-ttu-id="ed68f-177">Como este tutorial é sobre a interoperação e não sobre design de controle, o código completo para o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio é fornecido aqui como um bloco de código, sem instruções distintas para compilá-lo ou o que significa que cada parte.</span><span class="sxs-lookup"><span data-stu-id="ed68f-177">Since this tutorial is about interoperation and not about control design, complete code for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock is provided here as a code block, without discrete instructions for building it up or what each part means.</span></span> <span data-ttu-id="ed68f-178">Fique à vontade para testar este código para alterar a aparência ou a funcionalidade do controle.</span><span class="sxs-lookup"><span data-stu-id="ed68f-178">Feel free to experiment with this code to change the look and feel or functionality of the control.</span></span>

<span data-ttu-id="ed68f-179">Aqui está a marcação:</span><span class="sxs-lookup"><span data-stu-id="ed68f-179">Here is the markup:</span></span>

[!code-xaml[Win32Clock#AllClockXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]

<span data-ttu-id="ed68f-180">E aqui está o code-behind que acompanha:</span><span class="sxs-lookup"><span data-stu-id="ed68f-180">And here is the accompanying code-behind:</span></span>

[!code-csharp[Win32Clock#AllClockCS](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]

<span data-ttu-id="ed68f-181">O resultado final se parece com:</span><span class="sxs-lookup"><span data-stu-id="ed68f-181">The final result looks like:</span></span>

![Caixa de diálogo de propriedades de data e hora do resultado final](./media/walkthrough-hosting-a-wpf-clock-in-win32/final-result-date-time-properties-dialog.png)

<span data-ttu-id="ed68f-183">Para comparar seu resultado final com o código que produziu a captura de tela, consulte [exemplo de interoperação de relógio do Win32](https://go.microsoft.com/fwlink/?LinkID=160051).</span><span class="sxs-lookup"><span data-stu-id="ed68f-183">To compare your end result to the code that produced this screenshot, see [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051).</span></span>

## <a name="see-also"></a><span data-ttu-id="ed68f-184">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed68f-184">See also</span></span>

- <xref:System.Windows.Interop.HwndSource>
- [<span data-ttu-id="ed68f-185">Interoperação do WPF e do Win32</span><span class="sxs-lookup"><span data-stu-id="ed68f-185">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
- [<span data-ttu-id="ed68f-186">Exemplo de interoperação de relógio do Win32</span><span class="sxs-lookup"><span data-stu-id="ed68f-186">Win32 Clock Interoperation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160051)
