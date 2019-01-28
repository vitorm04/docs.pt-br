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
ms.openlocfilehash: 94c90ed264c40c99b0c139948578c85e8c9855d7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696341"
---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a>Como: usar invocação de plataforma para executar um arquivo wave (Guia de Programação em C#)
O exemplo de código C# a seguir ilustra como usar os serviços de invocação de plataforma para reproduzir um arquivo de som wave no sistema operacional Windows.  
  
## <a name="example"></a>Exemplo  
 Esse código de exemplo usa `DllImport` para importar o ponto de entrada de método `PlaySound` da `winmm.dll` como `Form1 PlaySound()`. O exemplo tem um Windows Form simples com um botão. Ao clicar no botão, abre-se uma caixa de diálogo padrão <xref:System.Windows.Forms.OpenFileDialog> do Windows para que você possa abrir o arquivo para reprodução. Quando um arquivo wave é selecionado, ele é executado usando o método `PlaySound()` da biblioteca `winmm.dll`. Para obter mais informações sobre esse método, consulte [Usando a função PlaySound com arquivos de áudio Waveform](https://docs.microsoft.com/windows/desktop/multimedia/using-playsound-to-play-waveform-audio-files). Procure e selecione um arquivo que tenha uma extensão .wav e, em seguida, clique em **Abrir** para reproduzir o arquivo wave usando a invocação de plataforma. Uma caixa de texto exibe o caminho completo do arquivo selecionado.  
  
 A caixa de diálogo **Abrir Arquivos** é filtrada por meio das configurações de filtro para mostrar somente os arquivos que têm uma extensão .wav:  
  
 [!code-csharp[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]  
  
 [!code-csharp[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
### <a name="to-compile-the-code"></a>Para compilar o código  
  
1.  Crie um novo projeto de aplicativos do Windows do C# no Visual Studio e dê o nome de **WinSound**.  
  
2.  Copie o código acima e cole-o sobre o conteúdo do arquivo `Form1.cs`.  
  
3.  Copie o seguinte código e cole-o no arquivo `Form1.Designer.cs`, no método `InitializeComponent()`, após qualquer código existente.  
  
     [!code-csharp[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]  
  
4.  Compile e execute o código.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Para obter mais informações, confira [Segurança no .NET](../../../standard/security/index.md).  
  
## <a name="see-also"></a>Consulte também

- [Guia de Programação em C#](../../../csharp/programming-guide/index.md)
- [Visão geral sobre interoperabilidade](../../../csharp/programming-guide/interop/interoperability-overview.md)
- [Um olhar detalhado sobre invocação de plataforma](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Marshaling de dados com a invocação de plataforma](../../../framework/interop/marshaling-data-with-platform-invoke.md)
