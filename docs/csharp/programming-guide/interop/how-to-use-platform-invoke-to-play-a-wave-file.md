---
title: 'Como: usar invocação de plataforma para executar um arquivo wave – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: 2d7f50952a485c09e74462f3ad731d710b8f9198
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65584268"
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a><span data-ttu-id="8157b-102">Como: usar invocação de plataforma para executar um arquivo wave (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="8157b-102">How to: Use Platform Invoke to Play a Wave File (C# Programming Guide)</span></span>
<span data-ttu-id="8157b-103">O exemplo de código C# a seguir ilustra como usar os serviços de invocação de plataforma para reproduzir um arquivo de som wave no sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="8157b-103">The following C# code example illustrates how to use platform invoke services to play a wave sound file on the Windows operating system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8157b-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8157b-104">Example</span></span>  
 <span data-ttu-id="8157b-105">Esse código de exemplo usa `DllImport` para importar o ponto de entrada de método `PlaySound` da `winmm.dll` como `Form1 PlaySound()`.</span><span class="sxs-lookup"><span data-stu-id="8157b-105">This example code uses `DllImport` to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="8157b-106">O exemplo tem um Windows Form simples com um botão.</span><span class="sxs-lookup"><span data-stu-id="8157b-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="8157b-107">Ao clicar no botão, abre-se uma caixa de diálogo padrão <xref:System.Windows.Forms.OpenFileDialog> do Windows para que você possa abrir o arquivo para reprodução.</span><span class="sxs-lookup"><span data-stu-id="8157b-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="8157b-108">Quando um arquivo wave é selecionado, ele é executado usando o método `PlaySound()` da biblioteca `winmm.dll`.</span><span class="sxs-lookup"><span data-stu-id="8157b-108">When a wave file is selected, it is played by using the `PlaySound()` method of the `winmm.dll` library.</span></span> <span data-ttu-id="8157b-109">Para obter mais informações sobre esse método, consulte [Usando a função PlaySound com arquivos de áudio Waveform](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span><span class="sxs-lookup"><span data-stu-id="8157b-109">For more information about this method, see [Using the PlaySound function with Waveform-Audio Files](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span></span> <span data-ttu-id="8157b-110">Procure e selecione um arquivo que tenha uma extensão .wav e, em seguida, clique em **Abrir** para reproduzir o arquivo wave usando a invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="8157b-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="8157b-111">Uma caixa de texto exibe o caminho completo do arquivo selecionado.</span><span class="sxs-lookup"><span data-stu-id="8157b-111">A text box shows the full path of the file selected.</span></span>  
  
 <span data-ttu-id="8157b-112">A caixa de diálogo **Abrir Arquivos** é filtrada por meio das configurações de filtro para mostrar somente os arquivos que têm uma extensão .wav:</span><span class="sxs-lookup"><span data-stu-id="8157b-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>  
  
 [!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]  
  
 [!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8157b-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="8157b-113">Compiling the Code</span></span>  
  
1. <span data-ttu-id="8157b-114">Crie um novo projeto de aplicativos do Windows do C# no Visual Studio e dê o nome de **WinSound**.</span><span class="sxs-lookup"><span data-stu-id="8157b-114">Create a new C# Windows Application project in Visual Studio and name it **WinSound**.</span></span>  
  
2. <span data-ttu-id="8157b-115">Copie o código acima e cole-o sobre o conteúdo do arquivo `Form1.cs`.</span><span class="sxs-lookup"><span data-stu-id="8157b-115">Copy the code above, and paste it over the contents of the `Form1.cs` file.</span></span>  
  
3. <span data-ttu-id="8157b-116">Copie o seguinte código e cole-o no arquivo `Form1.Designer.cs`, no método `InitializeComponent()`, após qualquer código existente.</span><span class="sxs-lookup"><span data-stu-id="8157b-116">Copy the following code, and paste it in the `Form1.Designer.cs` file, in the `InitializeComponent()` method, after any existing code.</span></span>  
  
     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]  
  
4. <span data-ttu-id="8157b-117">Compile e execute o código.</span><span class="sxs-lookup"><span data-stu-id="8157b-117">Compile and run the code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8157b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8157b-118">See also</span></span>

- [<span data-ttu-id="8157b-119">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="8157b-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="8157b-120">Visão geral sobre interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="8157b-120">Interoperability Overview</span></span>](../../../csharp/programming-guide/interop/interoperability-overview.md)
- [<span data-ttu-id="8157b-121">Um olhar detalhado sobre invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="8157b-121">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="8157b-122">Marshaling de dados com a invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="8157b-122">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
