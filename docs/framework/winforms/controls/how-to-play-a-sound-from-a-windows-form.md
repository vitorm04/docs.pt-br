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
# <a name="how-to-play-a-sound-from-a-windows-form"></a>Como: Reproduzir um som de um Windows Form
Este exemplo reproduz um som em um determinado caminho em tempo de execução.

## <a name="example"></a>Exemplo

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

## <a name="compiling-the-code"></a>Compilando o código
 Este exemplo requer:

- Se você substituir o nome `"c:\Windows\Media\chimes.wav"` do arquivo por um nome de arquivo válido.

- (C#) Uma referência ao <xref:System.Media?displayProperty=nameWithType> namespace.

## <a name="robust-programming"></a>Programação robusta
 As operações de arquivo devem ser colocadas entre os blocos de manipulação de exceção estruturada apropriados.

 As seguintes condições podem causar uma exceção:

- O nome do caminho está malformado. Por exemplo, ele contém caracteres inválidos ou é somente um espaço em branco (classe <xref:System.ArgumentException>).

- O caminho é somente leitura (<xref:System.IO.IOException> classe).

- O nome do caminho `null` é<xref:System.ArgumentNullException> (classe).

- O nome do caminho é muito longo<xref:System.IO.PathTooLongException> (classe).

- O caminho é inválido (<xref:System.IO.DirectoryNotFoundException> classe).

- O caminho é apenas um sinal de dois-pontos,<xref:System.NotSupportedException> ":" (classe).

## <a name="net-framework-security"></a>Segurança do .NET Framework
 Não tome decisões sobre o conteúdo do arquivo com base no nome do arquivo. Por exemplo, o arquivo `Form1.vb` pode não ser um arquivo de origem Visual Basic. Verifique todas as entradas antes de usar os dados no seu aplicativo.

## <a name="see-also"></a>Consulte também

- <xref:System.Media.SoundPlayer>
- [Como: Carregar um som de forma assíncrona em um formulário do Windows](how-to-load-a-sound-asynchronously-within-a-windows-form.md)
