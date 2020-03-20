---
title: 'Como: Abrir arquivos com o componente OpenFileDialog'
ms.date: 02/11/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: ca69de19ab1b9ae387002898145fe99e35a7b6b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182125"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a>Como: Abrir arquivos com o OpenFileDialog

O <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> componente abre a caixa de diálogo do Windows para navegar e selecionar arquivos. Para abrir e ler os arquivos <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> selecionados, você pode <xref:System.IO.StreamReader?displayProperty=nameWithType> usar o método ou criar uma instância da classe. Os exemplos a seguir mostram ambas as abordagens.

No .NET Framework, para <xref:System.Windows.Forms.FileDialog.FileName%2A> obter ou definir a <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> propriedade requer um nível de privilégio concedido pela classe. Os exemplos executam uma <xref:System.Security.Permissions.FileIOPermission> verificação de permissão e podem abrir uma exceção devido a privilégios insuficientes se executados em um contexto de confiança parcial. Para obter mais informações, consulte [Os fundamentos básicos de segurança de acesso ao código](../../misc/code-access-security-basics.md).

Você pode criar e executar esses exemplos como aplicativos .NET Framework a partir da linha de comando C# ou Visual Basic. Para obter mais informações, consulte [a construção da linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou Build a partir da linha de [comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

Começando com o .NET Core 3.0, você também pode criar e executar os exemplos como aplicativos Windows .NET Core a partir de uma pasta que tem um nome de pasta .NET Core Windows Forms * \<>.csproj* project file.

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a>Exemplo: Leia um arquivo como um fluxo com streamReader  
  
O exemplo a seguir <xref:System.Windows.Forms.Button> usa <xref:System.Windows.Forms.Control.Click> o manipulador de <xref:System.Windows.Forms.OpenFileDialog> eventos <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> do controle do Windows Forms para abrir o com o método. Depois que o usuário escolhe um arquivo e <xref:System.IO.StreamReader> seleciona **OK,** uma instância da classe lê o arquivo e exibe seu conteúdo na caixa de texto do formulário. Para obter mais informações sobre <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> a <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>leitura de fluxos de arquivos, consulte e .  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a>Exemplo: Abra um arquivo de uma seleção filtrada com openfile

O exemplo a <xref:System.Windows.Forms.Button> seguir <xref:System.Windows.Forms.Control.Click> usa o manipulador <xref:System.Windows.Forms.OpenFileDialog> de eventos do controle para abrir o com um filtro que mostra apenas arquivos de texto. Depois que o usuário escolhe um arquivo <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> de texto e seleciona **OK,** o método é usado para abrir o arquivo no Bloco de Notas.

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Confira também

- <xref:System.Windows.Forms.OpenFileDialog>
- [Componente OpenFileDialog](openfiledialog-component-windows-forms.md)
