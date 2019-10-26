---
title: 'Instruções passo a passo: hospedando um relógio do WPF em Win32'
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 42ed51a1a1ce59b6a3cc3319d86d3a7445403ce4
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919738"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a><span data-ttu-id="f3faf-102">Instruções passo a passo: hospedando um relógio do WPF em Win32</span><span class="sxs-lookup"><span data-stu-id="f3faf-102">Walkthrough: Hosting a WPF Clock in Win32</span></span>

<span data-ttu-id="f3faf-103">Para colocar [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dentro de aplicativos [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], use <xref:System.Windows.Interop.HwndSource>, que fornece o HWND que contém o conteúdo do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f3faf-103">To put [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] applications, use <xref:System.Windows.Interop.HwndSource>, which provides the HWND that contains your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="f3faf-104">Primeiro, você cria o <xref:System.Windows.Interop.HwndSource>, dando a ele parâmetros semelhantes à CreateWindow.</span><span class="sxs-lookup"><span data-stu-id="f3faf-104">First you create the <xref:System.Windows.Interop.HwndSource>, giving it parameters similar to CreateWindow.</span></span> <span data-ttu-id="f3faf-105">Em seguida, você informa o <xref:System.Windows.Interop.HwndSource> sobre o conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que você deseja dentro dele.</span><span class="sxs-lookup"><span data-stu-id="f3faf-105">Then you tell the <xref:System.Windows.Interop.HwndSource> about the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content you want inside it.</span></span> <span data-ttu-id="f3faf-106">Por fim, você obtém o HWND fora do <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="f3faf-106">Finally, you get the HWND out of the <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="f3faf-107">Este tutorial ilustra como criar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] misto dentro de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplicativo que reimplementa a caixa de diálogo **Propriedades de data e hora** do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="f3faf-107">This walkthrough illustrates how to create a mixed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application that reimplements the operating system **Date and Time Properties** dialog.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f3faf-108">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f3faf-108">Prerequisites</span></span>

<span data-ttu-id="f3faf-109">Consulte [Interoperação Win32 e WPF](wpf-and-win32-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="f3faf-109">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="how-to-use-this-tutorial"></a><span data-ttu-id="f3faf-110">Como usar esse tutorial</span><span class="sxs-lookup"><span data-stu-id="f3faf-110">How to Use This Tutorial</span></span>

<span data-ttu-id="f3faf-111">Este tutorial mostra as etapas importantes de produção de um aplicativo de interoperação.</span><span class="sxs-lookup"><span data-stu-id="f3faf-111">This tutorial concentrates on the important steps of producing an interoperation application.</span></span> <span data-ttu-id="f3faf-112">O tutorial é apoiado por um exemplo de exemplo de [interoperação de relógio do Win32](https://go.microsoft.com/fwlink/?LinkID=160051), mas esse exemplo é refletido do produto final.</span><span class="sxs-lookup"><span data-stu-id="f3faf-112">The tutorial is backed by a sample, [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051), but that sample is reflective of the end product.</span></span> <span data-ttu-id="f3faf-113">Este tutorial documenta as etapas como se você estivesse começando com um projeto [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] existente, talvez um projeto pré-existente, e estivesse adicionando um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hospedado ao seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f3faf-113">This tutorial documents the steps as if you were starting with an existing [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project of your own, perhaps a pre-existing project, and you were adding a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to your application.</span></span> <span data-ttu-id="f3faf-114">Você pode comparar seu produto final com o [exemplo de interoperação de relógio do Win32](https://go.microsoft.com/fwlink/?LinkID=160051).</span><span class="sxs-lookup"><span data-stu-id="f3faf-114">You can compare your end product with [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051).</span></span>

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a><span data-ttu-id="f3faf-115">Um passo a passo do Windows Presentation Framework no Win32 (HwndSource)</span><span class="sxs-lookup"><span data-stu-id="f3faf-115">A Walkthrough of Windows Presentation Framework Inside Win32 (HwndSource)</span></span>

<span data-ttu-id="f3faf-116">O gráfico a seguir mostra o produto final desejado deste tutorial:</span><span class="sxs-lookup"><span data-stu-id="f3faf-116">The following graphic shows the intended end product of this tutorial:</span></span>

![Captura de tela que mostra a caixa de diálogo Propriedades de data e hora.](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

<span data-ttu-id="f3faf-118">Você pode recriar essa caixa de diálogo criando C++ um projeto Win32 no Visual Studio e usando o editor de caixa de diálogo para criar o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f3faf-118">You can recreate this dialog by creating a C++ Win32 project in Visual Studio, and using the dialog editor to create the following:</span></span>

![Caixa de diálogo Propriedades de data e hora recriadas](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

<span data-ttu-id="f3faf-120">(Você não precisa usar o Visual Studio para usar <xref:System.Windows.Interop.HwndSource>e não precisa usar C++ o para escrever[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]programas, mas essa é uma maneira bastante comum de fazer isso e se presta bem a uma explicação do tutorial do gradual).</span><span class="sxs-lookup"><span data-stu-id="f3faf-120">(You do not need to use Visual Studio to use <xref:System.Windows.Interop.HwndSource>, and you do not need to use C++ to write [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programs, but this is a fairly typical way to do it, and lends itself well to a stepwise tutorial explanation).</span></span>

<span data-ttu-id="f3faf-121">Você precisa realizar cinco subetapas específicas para colocar um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio na caixa de diálogo:</span><span class="sxs-lookup"><span data-stu-id="f3faf-121">You need to accomplish five particular substeps in order to put a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock into the dialog:</span></span>

1. <span data-ttu-id="f3faf-122">Habilite seu projeto de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] para chamar o código gerenciado ( **/CLR**) alterando as configurações do projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f3faf-122">Enable your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project to call managed code (**/clr**) by changing project settings in Visual Studio.</span></span>

2. <span data-ttu-id="f3faf-123">Crie um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> em uma DLL separada.</span><span class="sxs-lookup"><span data-stu-id="f3faf-123">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> in a separate DLL.</span></span>

3. <span data-ttu-id="f3faf-124">Coloque esse [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> dentro de um <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="f3faf-124">Put that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> inside an <xref:System.Windows.Interop.HwndSource>.</span></span>

4. <span data-ttu-id="f3faf-125">Obtenha um HWND para esse <xref:System.Windows.Controls.Page> usando a propriedade <xref:System.Windows.Interop.HwndSource.Handle%2A>.</span><span class="sxs-lookup"><span data-stu-id="f3faf-125">Get an HWND for that <xref:System.Windows.Controls.Page> using the <xref:System.Windows.Interop.HwndSource.Handle%2A> property.</span></span>

5. <span data-ttu-id="f3faf-126">Use [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] para decidir onde posicionar o HWND dentro do aplicativo de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] maior</span><span class="sxs-lookup"><span data-stu-id="f3faf-126">Use [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] to decide where to place the HWND within the larger [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application</span></span>

## <a name="clr"></a><span data-ttu-id="f3faf-127">/clr</span><span class="sxs-lookup"><span data-stu-id="f3faf-127">/clr</span></span>

<span data-ttu-id="f3faf-128">A primeira etapa é transformar esse projeto de [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] não gerenciado em um que possa chamar código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f3faf-128">The first step is to turn this unmanaged [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project into one that can call managed code.</span></span> <span data-ttu-id="f3faf-129">Você usa a opção de compilador/CLR, que será vinculada às DLLs necessárias que você deseja usar e ajustará o método Main para uso com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f3faf-129">You use the /clr compiler option, which will link to the necessary DLLs you want to use, and adjust the Main method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>

<span data-ttu-id="f3faf-130">Para habilitar o uso de código gerenciado dentro do C++ projeto: clique com o botão direito do mouse no projeto win32clock e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="f3faf-130">To enable the use of managed code inside the C++ project: Right-click on win32clock project and select **Properties**.</span></span> <span data-ttu-id="f3faf-131">Na página de propriedades **geral** (o padrão), altere o suporte ao Common Language Runtime para `/clr`.</span><span class="sxs-lookup"><span data-stu-id="f3faf-131">On the **General** property page (the default), change Common Language Runtime support to `/clr`.</span></span>

<span data-ttu-id="f3faf-132">Em seguida, adicione referências às DLLs necessárias para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore. dll, PresentationFramework. dll, System. dll, WindowsBase. dll, UIAutomationProvider. dll e UIAutomationTypes. dll.</span><span class="sxs-lookup"><span data-stu-id="f3faf-132">Next, add references to DLLs necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll, PresentationFramework.dll, System.dll, WindowsBase.dll, UIAutomationProvider.dll, and UIAutomationTypes.dll.</span></span> <span data-ttu-id="f3faf-133">(Seguir as instruções pressupõe que o sistema operacional está instalado na unidade C:.)</span><span class="sxs-lookup"><span data-stu-id="f3faf-133">(Following instructions assume the operating system is installed on C: drive.)</span></span>

1. <span data-ttu-id="f3faf-134">Clique com o botão direito do mouse em projeto win32clock e selecione **referências...** e dentro dessa caixa de diálogo:</span><span class="sxs-lookup"><span data-stu-id="f3faf-134">Right-click win32clock project and select **References...**, and inside that dialog:</span></span>

2. <span data-ttu-id="f3faf-135">Clique com o botão direito do mouse em projeto win32clock e selecione **referências...** .</span><span class="sxs-lookup"><span data-stu-id="f3faf-135">Right-click win32clock project and select **References...**.</span></span>

3. <span data-ttu-id="f3faf-136">Clique em **Adicionar nova referência**, clique na guia procurar, digite C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll e clique em OK.</span><span class="sxs-lookup"><span data-stu-id="f3faf-136">Click **Add New Reference**, click Browse tab, enter C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, and click OK.</span></span>

4. <span data-ttu-id="f3faf-137">Repita para PresentationFramework.dll: C:\Arquivos de Programa\Assemblies de Referência\Microsoft\Framework\v3.0\PresentationFramework.dll.</span><span class="sxs-lookup"><span data-stu-id="f3faf-137">Repeat for PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span></span>

5. <span data-ttu-id="f3faf-138">Repita para WindowsBase.dll: C:\Arquivos de Programa\Assemblies de Referência\Microsoft\Framework\v3.0\WindowsBase.dll.</span><span class="sxs-lookup"><span data-stu-id="f3faf-138">Repeat for WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span></span>

6. <span data-ttu-id="f3faf-139">Repita para UIAutomationTypes.dll: C:\Arquivos de Programa\Assemblies de Referência\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span><span class="sxs-lookup"><span data-stu-id="f3faf-139">Repeat for UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span></span>

7. <span data-ttu-id="f3faf-140">Repita para UIAutomationProvider.dll: C:\Arquivos de Programa\Assemblies de Referência\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span><span class="sxs-lookup"><span data-stu-id="f3faf-140">Repeat for UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span></span>

8. <span data-ttu-id="f3faf-141">Clique em **Adicionar nova referência**, selecione System. dll e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="f3faf-141">Click **Add New Reference**, select System.dll, and click **OK**.</span></span>

9. <span data-ttu-id="f3faf-142">Clique em **OK** para sair das páginas de propriedades win32clock para adicionar referências.</span><span class="sxs-lookup"><span data-stu-id="f3faf-142">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>

 <span data-ttu-id="f3faf-143">Por fim, adicione o `STAThreadAttribute` ao método `_tWinMain` para uso com [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="f3faf-143">Finally, add the `STAThreadAttribute` to the `_tWinMain` method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span></span>

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

<span data-ttu-id="f3faf-144">Esse atributo informa ao Common Language Runtime (CLR) que quando ele é inicializado Component Object Model (COM), ele deve usar um STA (modelo de apartamento de thread único), que é necessário para [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (e [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="f3faf-144">This attribute tells the common language runtime (CLR) that when it initializes Component Object Model (COM), it should use a single threaded apartment model (STA), which is necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (and [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).</span></span>

## <a name="create-a-windows-presentation-framework-page"></a><span data-ttu-id="f3faf-145">Criar uma página do Windows Presentation Framework</span><span class="sxs-lookup"><span data-stu-id="f3faf-145">Create a Windows Presentation Framework Page</span></span>

<span data-ttu-id="f3faf-146">Em seguida, você cria uma DLL que define um [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>.</span><span class="sxs-lookup"><span data-stu-id="f3faf-146">Next, you create a DLL that defines a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="f3faf-147">Geralmente, é mais fácil criar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> como um aplicativo autônomo e escrever e depurar a parte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="f3faf-147">It’s often easiest to create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> as a standalone application, and write and debug the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion that way.</span></span> <span data-ttu-id="f3faf-148">Depois de concluído, esse projeto pode ser transformado em uma DLL clicando com o botão direito do mouse no projeto, clicando em **Propriedades**, indo para o aplicativo e alterando o tipo de saída para a biblioteca de classes do Windows.</span><span class="sxs-lookup"><span data-stu-id="f3faf-148">Once done, that project can be turned into a DLL by right-clicking the project, clicking on **Properties**, going to the Application, and changing Output type to Windows Class Library.</span></span>

<span data-ttu-id="f3faf-149">O projeto DLL [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pode então ser combinado com o projeto [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] (uma solução que contém dois projetos) – clique com o botão direito do mouse na solução, selecione **projeto Add\Existing**.</span><span class="sxs-lookup"><span data-stu-id="f3faf-149">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll project can then be combined with the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project (one solution that contains two projects) – right-click on the solution, select **Add\Existing Project**.</span></span>

<span data-ttu-id="f3faf-150">Para usar essa [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll do projeto [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], você precisa adicionar uma referência:</span><span class="sxs-lookup"><span data-stu-id="f3faf-150">To use that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll from the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project, you need to add a reference:</span></span>

1. <span data-ttu-id="f3faf-151">Clique com o botão direito do mouse em projeto win32clock e selecione **referências...** .</span><span class="sxs-lookup"><span data-stu-id="f3faf-151">Right-click win32clock project and select **References...**.</span></span>

2. <span data-ttu-id="f3faf-152">Clique em **Adicionar nova referência**.</span><span class="sxs-lookup"><span data-stu-id="f3faf-152">Click **Add New Reference**.</span></span>

3. <span data-ttu-id="f3faf-153">Clique na guia **projetos** . Selecione WPFClock e clique em OK.</span><span class="sxs-lookup"><span data-stu-id="f3faf-153">Click the **Projects** tab. Select WPFClock, click OK.</span></span>

4. <span data-ttu-id="f3faf-154">Clique em **OK** para sair das páginas de propriedades win32clock para adicionar referências.</span><span class="sxs-lookup"><span data-stu-id="f3faf-154">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>

## <a name="hwndsource"></a><span data-ttu-id="f3faf-155">HwndSource</span><span class="sxs-lookup"><span data-stu-id="f3faf-155">HwndSource</span></span>

<span data-ttu-id="f3faf-156">Em seguida, você usa <xref:System.Windows.Interop.HwndSource> para fazer com que o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> seja semelhante a um HWND.</span><span class="sxs-lookup"><span data-stu-id="f3faf-156">Next, you use <xref:System.Windows.Interop.HwndSource> to make the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> look like an HWND.</span></span> <span data-ttu-id="f3faf-157">Você adiciona este bloco de código a um arquivo C++:</span><span class="sxs-lookup"><span data-stu-id="f3faf-157">You add this block of code to a C++ file:</span></span>

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

 <span data-ttu-id="f3faf-158">Esse é uma parte grande do código que poderia ser explicada.</span><span class="sxs-lookup"><span data-stu-id="f3faf-158">This is a long piece of code that could use some explanation.</span></span> <span data-ttu-id="f3faf-159">A primeira parte é composta por várias cláusulas para que você não precise qualificar totalmente todas as chamadas:</span><span class="sxs-lookup"><span data-stu-id="f3faf-159">The first part is various clauses so that you do not need to fully qualify all the calls:</span></span>

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;
```

 <span data-ttu-id="f3faf-160">Em seguida, você define uma função que cria o conteúdo de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], coloca um <xref:System.Windows.Interop.HwndSource> em volta dele e retorna o HWND:</span><span class="sxs-lookup"><span data-stu-id="f3faf-160">Then you define a function that creates the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content, puts an <xref:System.Windows.Interop.HwndSource> around it, and returns the HWND:</span></span>

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

<span data-ttu-id="f3faf-161">Primeiro, você cria uma <xref:System.Windows.Interop.HwndSource>, cujos parâmetros são semelhantes à CreateWindow:</span><span class="sxs-lookup"><span data-stu-id="f3faf-161">First you create an <xref:System.Windows.Interop.HwndSource>, whose parameters are similar to CreateWindow:</span></span>

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

<span data-ttu-id="f3faf-162">Em seguida, você cria a classe de conteúdo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] chamando seu construtor:</span><span class="sxs-lookup"><span data-stu-id="f3faf-162">Then you create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content class by calling its constructor:</span></span>

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

<span data-ttu-id="f3faf-163">Em seguida, conecte a página à <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="f3faf-163">You then connect the page to the <xref:System.Windows.Interop.HwndSource>:</span></span>

```cpp
source->RootVisual = page;
```

 <span data-ttu-id="f3faf-164">E na linha final, retorne o HWND para o <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="f3faf-164">And in the final line, return the HWND for the <xref:System.Windows.Interop.HwndSource>:</span></span>

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a><span data-ttu-id="f3faf-165">Posicionamento do Hwnd</span><span class="sxs-lookup"><span data-stu-id="f3faf-165">Positioning the Hwnd</span></span>

<span data-ttu-id="f3faf-166">Agora que você tem um HWND que contém o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio, você precisa colocar esse HWND dentro da caixa de diálogo [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f3faf-166">Now that you have an HWND that contains the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you need to put that HWND inside the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog.</span></span> <span data-ttu-id="f3faf-167">Se você sabia apenas onde colocar o HWND, basta passar esse tamanho e o local para a função `GetHwnd` que você definiu anteriormente.</span><span class="sxs-lookup"><span data-stu-id="f3faf-167">If you knew just where to put the HWND, you would just pass that size and location to the `GetHwnd` function you defined earlier.</span></span> <span data-ttu-id="f3faf-168">Mas você usou um arquivo de recurso para definir a caixa de diálogo, então não tem muita certeza sobre onde os HWNDs estão posicionados.</span><span class="sxs-lookup"><span data-stu-id="f3faf-168">But you used a resource file to define the dialog, so you are not exactly sure where any of the HWNDs are positioned.</span></span> <span data-ttu-id="f3faf-169">Você pode usar o editor de caixa de diálogo do Visual Studio para colocar um [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] controle estático no qual deseja que o relógio fique ("Inserir relógio aqui") e usá-lo para posicionar o relógio de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f3faf-169">You can use the Visual Studio dialog editor to put a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] STATIC control where you want the clock to go ("Insert clock here"), and use that to position the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock.</span></span>

<span data-ttu-id="f3faf-170">Onde você lida com o WM_INITDIALOG, você usa `GetDlgItem` para recuperar o HWND para o espaço reservado estático:</span><span class="sxs-lookup"><span data-stu-id="f3faf-170">Where you handle WM_INITDIALOG, you use `GetDlgItem` to retrieve the HWND for the placeholder STATIC:</span></span>

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

<span data-ttu-id="f3faf-171">Em seguida, você calcula o tamanho e a posição desse espaço reservado estático, para que você possa colocar o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio nesse local:</span><span class="sxs-lookup"><span data-stu-id="f3faf-171">You then calculate the size and position of that placeholder STATIC, so you can put the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock in that place:</span></span>

<span data-ttu-id="f3faf-172">Retângulo RECT;</span><span class="sxs-lookup"><span data-stu-id="f3faf-172">RECT rectangle;</span></span>

```cpp
GetWindowRect(placeholder, &rectangle);
int width = rectangle.right - rectangle.left;
int height = rectangle.bottom - rectangle.top;
POINT point;
point.x = rectangle.left;
point.y = rectangle.top;
result = MapWindowPoints(NULL, hDlg, &point, 1);
```

<span data-ttu-id="f3faf-173">Em seguida, oculte o espaço reservado STATIC:</span><span class="sxs-lookup"><span data-stu-id="f3faf-173">Then you hide the placeholder STATIC:</span></span>

```cpp
ShowWindow(placeholder, SW_HIDE);
```

<span data-ttu-id="f3faf-174">E crie o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do relógio HWND nesse local:</span><span class="sxs-lookup"><span data-stu-id="f3faf-174">And create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock HWND in that location:</span></span>

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

<span data-ttu-id="f3faf-175">Para tornar o tutorial interessante e produzir um relógio de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] real, você precisará criar um controle de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] relógio neste ponto.</span><span class="sxs-lookup"><span data-stu-id="f3faf-175">To make the tutorial interesting, and to produce a real [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you will need to create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock control at this point.</span></span> <span data-ttu-id="f3faf-176">Você pode fazer isso basicamente na marcação, com apenas alguns manipuladores de eventos no code-behind.</span><span class="sxs-lookup"><span data-stu-id="f3faf-176">You can do so mostly in markup, with just a few event handlers in code-behind.</span></span> <span data-ttu-id="f3faf-177">Como este tutorial é sobre interoperação e não sobre design de controle, o código completo para o relógio de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] é fornecido aqui como um bloco de código, sem instruções discretas para criá-lo ou o que significa cada parte.</span><span class="sxs-lookup"><span data-stu-id="f3faf-177">Since this tutorial is about interoperation and not about control design, complete code for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock is provided here as a code block, without discrete instructions for building it up or what each part means.</span></span> <span data-ttu-id="f3faf-178">Fique à vontade para testar este código para alterar a aparência ou a funcionalidade do controle.</span><span class="sxs-lookup"><span data-stu-id="f3faf-178">Feel free to experiment with this code to change the look and feel or functionality of the control.</span></span>

<span data-ttu-id="f3faf-179">Aqui está a marcação:</span><span class="sxs-lookup"><span data-stu-id="f3faf-179">Here is the markup:</span></span>

[!code-xaml[Win32Clock#AllClockXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]

<span data-ttu-id="f3faf-180">E aqui está o code-behind que acompanha:</span><span class="sxs-lookup"><span data-stu-id="f3faf-180">And here is the accompanying code-behind:</span></span>

[!code-csharp[Win32Clock#AllClockCS](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]

<span data-ttu-id="f3faf-181">O resultado final se parece com:</span><span class="sxs-lookup"><span data-stu-id="f3faf-181">The final result looks like:</span></span>

![Caixa de diálogo Propriedades da data e hora final do resultado](./media/walkthrough-hosting-a-wpf-clock-in-win32/final-result-date-time-properties-dialog.png)

<span data-ttu-id="f3faf-183">Para comparar o resultado final ao código que produziu esta captura de tela, consulte [exemplo de interoperação de relógio Win32](https://go.microsoft.com/fwlink/?LinkID=160051).</span><span class="sxs-lookup"><span data-stu-id="f3faf-183">To compare your end result to the code that produced this screenshot, see [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051).</span></span>

## <a name="see-also"></a><span data-ttu-id="f3faf-184">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3faf-184">See also</span></span>

- <xref:System.Windows.Interop.HwndSource>
- [<span data-ttu-id="f3faf-185">Interoperação Win32 e WPF</span><span class="sxs-lookup"><span data-stu-id="f3faf-185">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
- [<span data-ttu-id="f3faf-186">Exemplo de interoperação de relógio do Win32</span><span class="sxs-lookup"><span data-stu-id="f3faf-186">Win32 Clock Interoperation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160051)
