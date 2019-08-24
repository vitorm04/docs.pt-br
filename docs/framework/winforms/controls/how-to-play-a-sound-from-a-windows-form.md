---
title: 'Como: Reproduzir um som de um Windows Form'
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
ms.openlocfilehash: 68a68f05b847877641132e540995f6b14bb6e065
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015796"
---
# <a name="how-to-play-a-sound-from-a-windows-form"></a><span data-ttu-id="388af-102">Como: Reproduzir um som de um Windows Form</span><span class="sxs-lookup"><span data-stu-id="388af-102">How to: Play a Sound from a Windows Form</span></span>
<span data-ttu-id="388af-103">Este exemplo reproduz um som em um determinado caminho em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="388af-103">This example plays a sound at a given path at run time.</span></span>

## <a name="example"></a><span data-ttu-id="388af-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="388af-104">Example</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="388af-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="388af-105">Compiling the Code</span></span>
 <span data-ttu-id="388af-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="388af-106">This example requires:</span></span>

- <span data-ttu-id="388af-107">Se você substituir o nome `"c:\Windows\Media\chimes.wav"` do arquivo por um nome de arquivo válido.</span><span class="sxs-lookup"><span data-stu-id="388af-107">That you replace the file name `"c:\Windows\Media\chimes.wav"` with a valid file name.</span></span>

- <span data-ttu-id="388af-108">(C#) Uma referência ao <xref:System.Media?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="388af-108">(C#) A reference to the <xref:System.Media?displayProperty=nameWithType> namespace.</span></span>

## <a name="robust-programming"></a><span data-ttu-id="388af-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="388af-109">Robust Programming</span></span>
 <span data-ttu-id="388af-110">As operações de arquivo devem ser colocadas entre os blocos de manipulação de exceção estruturada apropriados.</span><span class="sxs-lookup"><span data-stu-id="388af-110">File operations should be enclosed within appropriate structured exception handling blocks.</span></span>

 <span data-ttu-id="388af-111">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="388af-111">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="388af-112">O nome do caminho está malformado.</span><span class="sxs-lookup"><span data-stu-id="388af-112">The path name is malformed.</span></span> <span data-ttu-id="388af-113">Por exemplo, ele contém caracteres inválidos ou é somente um espaço em branco (classe <xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="388af-113">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span>

- <span data-ttu-id="388af-114">O caminho é somente leitura (<xref:System.IO.IOException> classe).</span><span class="sxs-lookup"><span data-stu-id="388af-114">The path is read-only (<xref:System.IO.IOException> class).</span></span>

- <span data-ttu-id="388af-115">O nome do caminho `null` é<xref:System.ArgumentNullException> (classe).</span><span class="sxs-lookup"><span data-stu-id="388af-115">The path name is `null` (<xref:System.ArgumentNullException> class).</span></span>

- <span data-ttu-id="388af-116">O nome do caminho é muito longo<xref:System.IO.PathTooLongException> (classe).</span><span class="sxs-lookup"><span data-stu-id="388af-116">The path name is too long (<xref:System.IO.PathTooLongException> class).</span></span>

- <span data-ttu-id="388af-117">O caminho é inválido (<xref:System.IO.DirectoryNotFoundException> classe).</span><span class="sxs-lookup"><span data-stu-id="388af-117">The path is invalid (<xref:System.IO.DirectoryNotFoundException> class).</span></span>

- <span data-ttu-id="388af-118">O caminho é apenas um sinal de dois-pontos,<xref:System.NotSupportedException> ":" (classe).</span><span class="sxs-lookup"><span data-stu-id="388af-118">The path is only a colon, ":" (<xref:System.NotSupportedException> class).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="388af-119">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="388af-119">.NET Framework Security</span></span>
 <span data-ttu-id="388af-120">Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="388af-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="388af-121">Por exemplo, o arquivo `Form1.vb` pode não ser um arquivo de origem Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="388af-121">For example, the file `Form1.vb` may not be a Visual Basic source file.</span></span> <span data-ttu-id="388af-122">Verifique todas as entradas antes de usar os dados no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="388af-122">Verify all inputs before using the data in your application.</span></span>

## <a name="see-also"></a><span data-ttu-id="388af-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="388af-123">See also</span></span>

- <xref:System.Media.SoundPlayer>
- [<span data-ttu-id="388af-124">Como: Carregar um som de forma assíncrona em um formulário do Windows</span><span class="sxs-lookup"><span data-stu-id="388af-124">How to: Load a Sound Asynchronously within a Windows Form</span></span>](how-to-load-a-sound-asynchronously-within-a-windows-form.md)
