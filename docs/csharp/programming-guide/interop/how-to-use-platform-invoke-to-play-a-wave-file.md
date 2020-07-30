---
title: Como usar a invocação de plataforma para reproduzir um arquivo WAV – guia de programação C#
description: Este exemplo de código C# ilustra como usar os serviços de invocação de plataforma para reproduzir um arquivo de som WAV no sistema operacional Windows.
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: b30cb08e2dcde0eb85e8d88a690ae24bf7ae7f22
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302978"
---
# <a name="how-to-use-platform-invoke-to-play-a-wav-file-c-programming-guide"></a><span data-ttu-id="244ac-103">Como usar a invocação de plataforma para reproduzir um arquivo WAV (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="244ac-103">How to use platform invoke to play a WAV file (C# Programming Guide)</span></span>

<span data-ttu-id="244ac-104">O exemplo de código C# a seguir ilustra como usar os serviços de invocação de plataforma para reproduzir um arquivo de som WAV no sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="244ac-104">The following C# code example illustrates how to use platform invoke services to play a WAV sound file on the Windows operating system.</span></span>

## <a name="example"></a><span data-ttu-id="244ac-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="244ac-105">Example</span></span>

<span data-ttu-id="244ac-106">Esse código de exemplo usa <xref:System.Runtime.InteropServices.DllImportAttribute> para importar o ponto de entrada de método `PlaySound` da `winmm.dll` como `Form1 PlaySound()`.</span><span class="sxs-lookup"><span data-stu-id="244ac-106">This example code uses <xref:System.Runtime.InteropServices.DllImportAttribute> to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="244ac-107">O exemplo tem um Windows Form simples com um botão.</span><span class="sxs-lookup"><span data-stu-id="244ac-107">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="244ac-108">Ao clicar no botão, abre-se uma caixa de diálogo padrão <xref:System.Windows.Forms.OpenFileDialog> do Windows para que você possa abrir o arquivo para reprodução.</span><span class="sxs-lookup"><span data-stu-id="244ac-108">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="244ac-109">Quando um arquivo Wave é selecionado, ele é reproduzido usando o `PlaySound()` método da biblioteca de *winmm.dll* .</span><span class="sxs-lookup"><span data-stu-id="244ac-109">When a wave file is selected, it is played by using the `PlaySound()` method of the *winmm.dll* library.</span></span> <span data-ttu-id="244ac-110">Para obter mais informações sobre esse método, consulte [Usando a função PlaySound com arquivos de áudio Waveform](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span><span class="sxs-lookup"><span data-stu-id="244ac-110">For more information about this method, see [Using the PlaySound function with Waveform-Audio Files](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files).</span></span> <span data-ttu-id="244ac-111">Procure e selecione um arquivo que tenha uma extensão .wav e, em seguida, clique em **Abrir** para reproduzir o arquivo wave usando a invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="244ac-111">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="244ac-112">Uma caixa de texto exibe o caminho completo do arquivo selecionado.</span><span class="sxs-lookup"><span data-stu-id="244ac-112">A text box shows the full path of the file selected.</span></span>

<span data-ttu-id="244ac-113">A caixa de diálogo **Abrir Arquivos** é filtrada por meio das configurações de filtro para mostrar somente os arquivos que têm uma extensão .wav:</span><span class="sxs-lookup"><span data-stu-id="244ac-113">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a><span data-ttu-id="244ac-114">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="244ac-114">Compiling the code</span></span>

1. <span data-ttu-id="244ac-115">Crie um novo projeto de aplicativo Windows Forms em C# no Visual Studio e nomeie-o **WinSound**.</span><span class="sxs-lookup"><span data-stu-id="244ac-115">Create a new C# Windows Forms Application project in Visual Studio and name it **WinSound**.</span></span>

2. <span data-ttu-id="244ac-116">Copie o código acima e cole-o sobre o conteúdo do arquivo *Form1.cs* .</span><span class="sxs-lookup"><span data-stu-id="244ac-116">Copy the code above, and paste it over the contents of the *Form1.cs* file.</span></span>

3. <span data-ttu-id="244ac-117">Copie o código a seguir e cole-o no arquivo *Form1.designer.cs* , no `InitializeComponent()` método, após qualquer código existente.</span><span class="sxs-lookup"><span data-stu-id="244ac-117">Copy the following code, and paste it in the *Form1.Designer.cs* file, in the `InitializeComponent()` method, after any existing code.</span></span>

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. <span data-ttu-id="244ac-118">Compile e execute o código.</span><span class="sxs-lookup"><span data-stu-id="244ac-118">Compile and run the code.</span></span>

## <a name="see-also"></a><span data-ttu-id="244ac-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="244ac-119">See also</span></span>

- [<span data-ttu-id="244ac-120">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="244ac-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="244ac-121">Visão geral sobre interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="244ac-121">Interoperability Overview</span></span>](interoperability-overview.md)
- [<span data-ttu-id="244ac-122">Um olhar detalhado sobre invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="244ac-122">A Closer Look at Platform Invoke</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [<span data-ttu-id="244ac-123">Marshaling de dados com invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="244ac-123">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)
