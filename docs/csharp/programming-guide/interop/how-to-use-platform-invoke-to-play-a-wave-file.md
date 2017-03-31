---
title: "Como usar invocação de plataforma para executar um arquivo wave (Guia de programação em C#) | Microsoft Docs"
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5415fc55fa193964fb4ae366c06ff4724d9b32ec
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-use-platform-invoke-to-play-a-wave-file-c-programming-guide"></a>Como usar invocação de plataforma para executar um arquivo wave (Guia de Programação em C#)
O exemplo de código C# a seguir ilustra como usar os serviços de invocação de plataforma para reproduzir um arquivo de som wave no sistema operacional Windows.  
  
## <a name="example"></a>Exemplo  
 Esse código de exemplo usa `DllImport` para importar o ponto de entrada de método `PlaySound` da `winmm.dll` como `Form1 PlaySound()`. O exemplo tem um Windows Form simples com um botão. Ao clicar no botão, abre-se uma caixa de diálogo padrão <xref:System.Windows.Forms.OpenFileDialog> do Windows para que você possa abrir o arquivo para reprodução. Quando um arquivo wave é selecionado, ele é executado usando o método `PlaySound()` do método de assembly da winmm.DLL. Para obter mais informações sobre o método `PlaySound` da winmm.dll, consulte [Usando a função PlaySound com arquivos de áudio Waveform](http://go.microsoft.com/fwlink/?LinkId=148553). Procure e selecione um arquivo que tenha uma extensão .wav e, em seguida, clique em **Abrir** para reproduzir o arquivo wave usando a invocação de plataforma. Uma caixa de texto exibe o caminho completo do arquivo selecionado.  
  
 A caixa de diálogo **Abrir Arquivos** é filtrada por meio das configurações de filtro para mostrar somente os arquivos que têm uma extensão .wav:  
  
 [!code-cs[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_1.cs)]  
  
 [!code-cs[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_2.cs)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
### <a name="to-compile-the-code"></a>Para compilar o código  
  
1.  Crie um novo projeto de aplicativos do Windows do C# no Visual Studio e dê o nome de **WinSound**.  
  
2.  Copie o código acima e cole-o sobre o conteúdo do arquivo `Form1.cs`.  
  
3.  Copie o seguinte código e cole-o no arquivo `Form1.Designer.cs`, no método `InitializeComponent()`, após qualquer código existente.  
  
     [!code-cs[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-use-platform-invoke-to-play-a-wave-file_3.cs)]  
  
4.  Compile e execute o código.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Para obter mais informações, consulte [Segurança do .NET Framework](http://go.microsoft.com/fwlink/?LinkId=37122).  
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Visão geral sobre interoperabilidade](../../../csharp/programming-guide/interop/interoperability-overview.md)   
 [Visão geral sobre interoperabilidade](../../../csharp/programming-guide/interop/interoperability-overview.md)   
 [Visão aprofundada da invocação de plataforma](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)   
 [Marshaling de dados com a invocação de plataforma](http://msdn.microsoft.com/library/dc5c76cf-7b12-406f-b79c-d1a023ec245d)
