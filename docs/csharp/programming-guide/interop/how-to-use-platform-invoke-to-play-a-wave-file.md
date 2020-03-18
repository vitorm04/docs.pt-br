---
title: Como usar a plataforma para reprodução de um arquivo WAV - C# Guia de Programação
ms.date: 07/20/2015
helpviewer_keywords:
- platform invoke, sound files
- interoperability [C#], playing WAV files using pinvoke
- wav files
- .wav files
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
ms.openlocfilehash: 3ea90f0739ad45c31e4f25836c9de8e708dff2cc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75700816"
---
# <a name="how-to-use-platform-invoke-to-play-a-wav-file-c-programming-guide"></a>Como usar a plataforma para reprodução de um arquivo WAV (C# Programming Guide)

O exemplo de código C# a seguir ilustra como usar os serviços de invocação da plataforma para reproduzir um arquivo de som WAV no sistema operacional Windows.

## <a name="example"></a>Exemplo

Esse código de exemplo usa <xref:System.Runtime.InteropServices.DllImportAttribute> para importar o ponto de entrada de método `PlaySound` da `winmm.dll` como `Form1 PlaySound()`. O exemplo tem um Windows Form simples com um botão. Ao clicar no botão, abre-se uma caixa de diálogo padrão <xref:System.Windows.Forms.OpenFileDialog> do Windows para que você possa abrir o arquivo para reprodução. Quando um arquivo de onda é `PlaySound()` selecionado, ele é reproduzido usando o método da biblioteca *winmm.dll.* Para obter mais informações sobre esse método, consulte [Usando a função PlaySound com arquivos de áudio Waveform](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files). Procure e selecione um arquivo que tenha uma extensão .wav e, em seguida, clique em **Abrir** para reproduzir o arquivo wave usando a invocação de plataforma. Uma caixa de texto exibe o caminho completo do arquivo selecionado.

A caixa de diálogo **Abrir Arquivos** é filtrada por meio das configurações de filtro para mostrar somente os arquivos que têm uma extensão .wav:

[!code-csharp[csProgGuideInterop#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#5)]

[!code-csharp[csProgGuideInterop#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#3)]

## <a name="compiling-the-code"></a>Compilando o código

1. Crie um novo projeto c# windows forms application no Visual Studio e nomeie-o **WinSound**.

2. Copie o código acima e cole-o sobre o conteúdo do arquivo *Form1.cs.*

3. Copie o seguinte código e cole-o no `InitializeComponent()` arquivo *Form1.Designer.cs,* no método, após qualquer código existente.

     [!code-csharp[csProgGuideInterop#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/WinSound.cs#4)]

4. Compile e execute o código.

## <a name="see-also"></a>Confira também

- [C# Guia de Programação](../index.md)
- [Visão geral sobre interoperabilidade](interoperability-overview.md)
- [Um olhar detalhado sobre invocação de plataforma](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Marshaling de dados com invocação de plataforma](../../../framework/interop/marshaling-data-with-platform-invoke.md)
