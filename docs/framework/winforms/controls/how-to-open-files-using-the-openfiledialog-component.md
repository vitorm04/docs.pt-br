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
ms.openlocfilehash: 5781543a61d77ef8f0658e95759c57fdb77cfc4f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723082"
---
# <a name="how-to-open-files-with-the-openfiledialog"></a>Como: Abrir arquivos com OpenFileDialog 

O <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> componente abre a caixa de diálogo do Windows para procurar e selecionar os arquivos. Para abrir e ler os arquivos selecionados, você pode usar o <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> método, ou crie uma instância da <xref:System.IO.StreamReader?displayProperty=nameWithType> classe. Os exemplos a seguir mostram as duas abordagens. 

No .NET Framework, para obter ou definir a <xref:System.Windows.Forms.FileDialog.FileName%2A> propriedade requer um nível de privilégio concedido pela <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> classe. Os exemplos executam um <xref:System.Security.Permissions.FileIOPermission> permissão verificar e pode lançar uma exceção devido a privilégios insuficientes se executado em um contexto de confiança parcial. Para obter mais informações, consulte [Noções básicas sobre segurança de acesso do código](../../misc/code-access-security-basics.md).

Você pode compilar e executar esses exemplos que os aplicativos do .NET Framework a C# ou a linha de comando do Visual Basic. Para obter mais informações, consulte [linha de comando compilando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou [compilar da linha de comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md). 

Começando com o .NET Core 3.0, você pode também compilar e executar os exemplos de como os aplicativos .NET Core do Windows de uma pasta que tem um .NET Core Windows Forms  *\<nome da pasta >. csproj* arquivo de projeto. 

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a>Exemplo: Ler um arquivo como um fluxo com um StreamReader  
  
O exemplo a seguir usa o Windows Forms <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Click> manipulador de eventos para abrir o <xref:System.Windows.Forms.OpenFileDialog> com o <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> método. Depois que o usuário escolhe um arquivo e seleciona **Okey**, uma instância da <xref:System.IO.StreamReader> classe lê o arquivo e exibe seu conteúdo na caixa de texto do formulário. Para obter mais informações sobre a leitura de fluxos de arquivos, consulte <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> e <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a>Exemplo: Abrir um arquivo de uma seleção filtrada com OpenFile 

O exemplo a seguir usa o <xref:System.Windows.Forms.Button> do controle <xref:System.Windows.Forms.Control.Click> manipulador de eventos para abrir o <xref:System.Windows.Forms.OpenFileDialog> com um filtro que mostra apenas os arquivos de texto. Depois que o usuário escolhe um arquivo de texto e seleciona **Okey**, o <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> método é usado para abrir o arquivo no bloco de notas.

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a>Consulte também
- <xref:System.Windows.Forms.OpenFileDialog>
- [Componente OpenFileDialog](openfiledialog-component-windows-forms.md)
