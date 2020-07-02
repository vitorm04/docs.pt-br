---
title: Como executar um som a partir de um Windows Form
description: Saiba como reproduzir um som de um Windows Form em um determinado caminho no tempo de execução. Além disso, saiba mais sobre como compilar o código e a estrutura de segurança do .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playing sounds [Windows Forms], Windows Forms
- sounds [Windows Forms], playing
- sounds
- My.Computer.Audio object [Windows Forms], playing sounds
- examples [Windows Forms], sounds
ms.assetid: 3d3350b7-1ebd-4e05-a738-48ca1160a19d
ms.openlocfilehash: beb17d994e224f41b2b590ecb1401988cdad314d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613742"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a><span data-ttu-id="586c4-104">Como executar um som a partir de um Windows Form</span><span class="sxs-lookup"><span data-stu-id="586c4-104">How to: Play a Sound from a Windows Form</span></span>
<span data-ttu-id="586c4-105">Este exemplo reproduz um som em um determinado caminho em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="586c4-105">This example plays a sound at a given path at run time.</span></span>

## <a name="example"></a><span data-ttu-id="586c4-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="586c4-106">Example</span></span>

```vb
Sub PlaySimpleSound()
    My.Computer.Audio.Play("c:\Windows\Media\chimes.wav")
End Sub
```

```csharp
private void playSimpleSound()
{
    SoundPlayer simpleSound = new SoundPlayer(@"c:\Windows\Media\chimes.wav");
    simpleSound.Play();
}
```

## <a name="compiling-the-code"></a><span data-ttu-id="586c4-107">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="586c4-107">Compiling the Code</span></span>
 <span data-ttu-id="586c4-108">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="586c4-108">This example requires:</span></span>

- <span data-ttu-id="586c4-109">Se você substituir o nome do arquivo `"c:\Windows\Media\chimes.wav"` por um nome de arquivo válido.</span><span class="sxs-lookup"><span data-stu-id="586c4-109">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>

- <span data-ttu-id="586c4-110">C# Uma referência ao <xref:System.Media?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="586c4-110">(C#) A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="586c4-111">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="586c4-111">Robust Programming</span></span>
 <span data-ttu-id="586c4-112">As operações de arquivo devem ser colocadas entre os blocos de manipulação de exceção estruturada apropriados.</span><span class="sxs-lookup"><span data-stu-id="586c4-112">File operations should be enclosed within appropriate structured exception handling blocks.</span></span>

 <span data-ttu-id="586c4-113">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="586c4-113">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="586c4-114">O nome do caminho está malformado.</span><span class="sxs-lookup"><span data-stu-id="586c4-114">The path name is malformed.</span></span> <span data-ttu-id="586c4-115">Por exemplo, ele contém caracteres inválidos ou é somente um espaço em branco (classe <xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="586c4-115">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span>

- <span data-ttu-id="586c4-116">O caminho é somente leitura ( <xref:System.IO.IOException> classe).</span><span class="sxs-lookup"><span data-stu-id="586c4-116">The path is read-only (<xref:System.IO.IOException> class).</span></span>

- <span data-ttu-id="586c4-117">O nome do caminho é `null` ( <xref:System.ArgumentNullException> classe).</span><span class="sxs-lookup"><span data-stu-id="586c4-117">The path name is `null` (<xref:System.ArgumentNullException> class).</span></span>

- <span data-ttu-id="586c4-118">O nome do caminho é muito longo ( <xref:System.IO.PathTooLongException> classe).</span><span class="sxs-lookup"><span data-stu-id="586c4-118">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>

- <span data-ttu-id="586c4-119">O caminho é inválido ( <xref:System.IO.DirectoryNotFoundException> classe).</span><span class="sxs-lookup"><span data-stu-id="586c4-119">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>

- <span data-ttu-id="586c4-120">O caminho é apenas um sinal de dois-pontos, ":" ( <xref:System.NotSupportedException> classe).</span><span class="sxs-lookup"><span data-stu-id="586c4-120">The path is only a colon, ":" (<xref:System.NotSupportedException> class).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="586c4-121">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="586c4-121">.NET Framework Security</span></span>
 <span data-ttu-id="586c4-122">Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="586c4-122">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="586c4-123">Por exemplo, o arquivo `Form1.vb` pode não ser um arquivo de origem Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="586c4-123">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="586c4-124">Verifique todas as entradas antes de usar os dados no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="586c4-124">Verify all inputs before using the data in your application.</span></span>

## <a name="see-also"></a><span data-ttu-id="586c4-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="586c4-125">See also</span></span>

- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="586c4-126">Como carregar um som de forma assíncrona dentro de um Windows Form</span><span class="sxs-lookup"><span data-stu-id="586c4-126">How to: Load a Sound Asynchronously within a Windows Form</span></span>](how-to-load-a-sound-asynchronously-within-a-windows-form.md)
