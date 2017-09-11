---
title: "Como usar invocação de plataforma para executar um arquivo wave (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 001236392d2b3d3c70dbd0faf2a899929dfe8625
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a><span data-ttu-id="2ee99-102">Como usar invocação de plataforma para executar um arquivo wave (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="2ee99-102">How to: Use Platform Invoke to Play a Wave File (C# Programming Guide)</span></span>
<span data-ttu-id="2ee99-103">O exemplo de código C# a seguir ilustra como usar os serviços de invocação de plataforma para reproduzir um arquivo de som wave no sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="2ee99-103">The following C# code example illustrates how to use platform invoke services to play a wave sound file on the Windows operating system.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ee99-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2ee99-104">Example</span></span>  
 <span data-ttu-id="2ee99-105">Esse código de exemplo usa `DllImport` para importar o ponto de entrada de método `PlaySound` da `winmm.dll` como `Form1 PlaySound()`.</span><span class="sxs-lookup"><span data-stu-id="2ee99-105">This example code uses `DllImport` to import `winmm.dll`'s `PlaySound` method entry point as `Form1 PlaySound()`.</span></span> <span data-ttu-id="2ee99-106">O exemplo tem um Windows Form simples com um botão.</span><span class="sxs-lookup"><span data-stu-id="2ee99-106">The example has a simple Windows Form with a button.</span></span> <span data-ttu-id="2ee99-107">Ao clicar no botão, abre-se uma caixa de diálogo padrão <xref:System.Windows.Forms.OpenFileDialog> do Windows para que você possa abrir o arquivo para reprodução.</span><span class="sxs-lookup"><span data-stu-id="2ee99-107">Clicking the button opens a standard windows <xref:System.Windows.Forms.OpenFileDialog> dialog box so that you can open a file to play.</span></span> <span data-ttu-id="2ee99-108">Quando um arquivo wave é selecionado, ele é executado usando o método `PlaySound()` do método de assembly da winmm.DLL.</span><span class="sxs-lookup"><span data-stu-id="2ee99-108">When a wave file is selected, it is played by using the `PlaySound()` method of the winmm.DLL assembly method.</span></span> <span data-ttu-id="2ee99-109">Para obter mais informações sobre o método `PlaySound` da winmm.dll, consulte [Usando a função PlaySound com arquivos de áudio Waveform](http://go.microsoft.com/fwlink/?LinkId=148553).</span><span class="sxs-lookup"><span data-stu-id="2ee99-109">For more information about winmm.dll's `PlaySound` method, see [Using the PlaySound function with Waveform-Audio Files](http://go.microsoft.com/fwlink/?LinkId=148553).</span></span> <span data-ttu-id="2ee99-110">Procure e selecione um arquivo que tenha uma extensão .wav e, em seguida, clique em **Abrir** para reproduzir o arquivo wave usando a invocação de plataforma.</span><span class="sxs-lookup"><span data-stu-id="2ee99-110">Browse and select a file that has a .wav extension, and then click **Open** to play the wave file by using platform invoke.</span></span> <span data-ttu-id="2ee99-111">Uma caixa de texto exibe o caminho completo do arquivo selecionado.</span><span class="sxs-lookup"><span data-stu-id="2ee99-111">A text box shows the full path of the file selected.</span></span>  
  
 <span data-ttu-id="2ee99-112">A caixa de diálogo **Abrir Arquivos** é filtrada por meio das configurações de filtro para mostrar somente os arquivos que têm uma extensão .wav:</span><span class="sxs-lookup"><span data-stu-id="2ee99-112">The **Open Files** dialog box is filtered to show only files that have a .wav extension through the filter settings:</span></span>  
  
 <span data-ttu-id="2ee99-113">[!code-cs[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="2ee99-113">[!code-cs[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]</span></span>  
  
 <span data-ttu-id="2ee99-114">[!code-cs[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="2ee99-114">[!code-cs[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2ee99-115">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="2ee99-115">Compiling the Code</span></span>  
  
### <a name="to-compile-the-code"></a><span data-ttu-id="2ee99-116">Para compilar o código</span><span class="sxs-lookup"><span data-stu-id="2ee99-116">To compile the code</span></span>  
  
1.  <span data-ttu-id="2ee99-117">Crie um novo projeto de aplicativos do Windows do C# no Visual Studio e dê o nome de **WinSound**.</span><span class="sxs-lookup"><span data-stu-id="2ee99-117">Create a new C# Windows Application project in Visual Studio and name it **WinSound**.</span></span>  
  
2.  <span data-ttu-id="2ee99-118">Copie o código acima e cole-o sobre o conteúdo do arquivo `Form1.cs`.</span><span class="sxs-lookup"><span data-stu-id="2ee99-118">Copy the code above, and paste it over the contents of the `Form1.cs` file.</span></span>  
  
3.  <span data-ttu-id="2ee99-119">Copie o seguinte código e cole-o no arquivo `Form1.Designer.cs`, no método `InitializeComponent()`, após qualquer código existente.</span><span class="sxs-lookup"><span data-stu-id="2ee99-119">Copy the following code, and paste it in the `Form1.Designer.cs` file, in the `InitializeComponent()` method, after any existing code.</span></span>  
  
     <span data-ttu-id="2ee99-120">[!code-cs[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="2ee99-120">[!code-cs[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]</span></span>  
  
4.  <span data-ttu-id="2ee99-121">Compile e execute o código.</span><span class="sxs-lookup"><span data-stu-id="2ee99-121">Compile and run the code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2ee99-122">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2ee99-122">.NET Framework Security</span></span>  
 <span data-ttu-id="2ee99-123">Para obter mais informações, consulte [Segurança do .NET Framework](http://go.microsoft.com/fwlink/?LinkId=37122).</span><span class="sxs-lookup"><span data-stu-id="2ee99-123">For more information, see [.NET Framework Security](http://go.microsoft.com/fwlink/?LinkId=37122).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ee99-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ee99-124">See Also</span></span>  
 <span data-ttu-id="2ee99-125">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="2ee99-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="2ee99-126">[Visão geral sobre interoperabilidade](../../../csharp/programming-guide/interop/interoperability-overview.md) </span><span class="sxs-lookup"><span data-stu-id="2ee99-126">[Interoperability Overview](../../../csharp/programming-guide/interop/interoperability-overview.md) </span></span>  
 <span data-ttu-id="2ee99-127">[Visão geral sobre interoperabilidade](../../../csharp/programming-guide/interop/interoperability-overview.md) </span><span class="sxs-lookup"><span data-stu-id="2ee99-127">[Interoperability Overview](../../../csharp/programming-guide/interop/interoperability-overview.md) </span></span>  
 <span data-ttu-id="2ee99-128">[Visão aprofundada da invocação de plataforma](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243) </span><span class="sxs-lookup"><span data-stu-id="2ee99-128">[A Closer Look at Platform Invoke](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243) </span></span>  
 [<span data-ttu-id="2ee99-129">Marshaling de dados com a invocação de plataforma</span><span class="sxs-lookup"><span data-stu-id="2ee99-129">Marshaling Data with Platform Invoke</span></span>](../../../framework/interop/marshaling-data-with-platform-invoke.md)

