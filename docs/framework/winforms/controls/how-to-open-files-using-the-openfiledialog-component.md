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
# <a name="how-to-open-files-with-the-openfiledialog"></a><span data-ttu-id="d9731-102">Como: Abrir arquivos com o OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="d9731-102">How to: Open files with the OpenFileDialog</span></span>

<span data-ttu-id="d9731-103">O <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> componente abre a caixa de diálogo do Windows para navegar e selecionar arquivos.</span><span class="sxs-lookup"><span data-stu-id="d9731-103">The <xref:System.Windows.Forms.OpenFileDialog?displayProperty=nameWithType> component opens the Windows dialog box for browsing and selecting files.</span></span> <span data-ttu-id="d9731-104">Para abrir e ler os arquivos <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> selecionados, você pode <xref:System.IO.StreamReader?displayProperty=nameWithType> usar o método ou criar uma instância da classe.</span><span class="sxs-lookup"><span data-stu-id="d9731-104">To open and read the selected files, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A?displayProperty=nameWithType> method, or create an instance of the <xref:System.IO.StreamReader?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="d9731-105">Os exemplos a seguir mostram ambas as abordagens.</span><span class="sxs-lookup"><span data-stu-id="d9731-105">The following examples show both approaches.</span></span>

<span data-ttu-id="d9731-106">No .NET Framework, para <xref:System.Windows.Forms.FileDialog.FileName%2A> obter ou definir a <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> propriedade requer um nível de privilégio concedido pela classe.</span><span class="sxs-lookup"><span data-stu-id="d9731-106">In .NET Framework, to get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="d9731-107">Os exemplos executam uma <xref:System.Security.Permissions.FileIOPermission> verificação de permissão e podem abrir uma exceção devido a privilégios insuficientes se executados em um contexto de confiança parcial.</span><span class="sxs-lookup"><span data-stu-id="d9731-107">The examples run a <xref:System.Security.Permissions.FileIOPermission> permission check, and can throw an exception due to insufficient privileges if run in a partial-trust context.</span></span> <span data-ttu-id="d9731-108">Para obter mais informações, consulte [Os fundamentos básicos de segurança de acesso ao código](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="d9731-108">For more information, see [Code access security basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="d9731-109">Você pode criar e executar esses exemplos como aplicativos .NET Framework a partir da linha de comando C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d9731-109">You can build and run these examples as .NET Framework apps from the C# or Visual Basic command line.</span></span> <span data-ttu-id="d9731-110">Para obter mais informações, consulte [a construção da linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou Build a partir da linha de [comando](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="d9731-110">For more information, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>

<span data-ttu-id="d9731-111">Começando com o .NET Core 3.0, você também pode criar e executar os exemplos como aplicativos Windows .NET Core a partir de uma pasta que tem um nome de pasta .NET Core Windows Forms \* \<>.csproj\* project file.</span><span class="sxs-lookup"><span data-stu-id="d9731-111">Starting with .NET Core 3.0, you can also build and run the examples as Windows .NET Core apps from a folder that has a .NET Core Windows Forms *\<folder name>.csproj* project file.</span></span>

## <a name="example-read-a-file-as-a-stream-with-streamreader"></a><span data-ttu-id="d9731-112">Exemplo: Leia um arquivo como um fluxo com streamReader</span><span class="sxs-lookup"><span data-stu-id="d9731-112">Example: Read a file as a stream with StreamReader</span></span>  
  
<span data-ttu-id="d9731-113">O exemplo a seguir <xref:System.Windows.Forms.Button> usa <xref:System.Windows.Forms.Control.Click> o manipulador de <xref:System.Windows.Forms.OpenFileDialog> eventos <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> do controle do Windows Forms para abrir o com o método.</span><span class="sxs-lookup"><span data-stu-id="d9731-113">The following example uses the Windows Forms <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="d9731-114">Depois que o usuário escolhe um arquivo e <xref:System.IO.StreamReader> seleciona **OK,** uma instância da classe lê o arquivo e exibe seu conteúdo na caixa de texto do formulário.</span><span class="sxs-lookup"><span data-stu-id="d9731-114">After the user chooses a file and selects **OK**, an instance of the <xref:System.IO.StreamReader> class reads the file and displays its contents in the form's text box.</span></span> <span data-ttu-id="d9731-115">Para obter mais informações sobre <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> a <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>leitura de fluxos de arquivos, consulte e .</span><span class="sxs-lookup"><span data-stu-id="d9731-115">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A?displayProperty=nameWithType> and <xref:System.IO.FileStream.Read%2A?displayProperty=nameWithType>.</span></span>  

 [!code-csharp[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#1](~/samples/snippets/winforms/open-files/example1/vb/Form1.vb)]  

## <a name="example-open-a-file-from-a-filtered-selection-with-openfile"></a><span data-ttu-id="d9731-116">Exemplo: Abra um arquivo de uma seleção filtrada com openfile</span><span class="sxs-lookup"><span data-stu-id="d9731-116">Example: Open a file from a filtered selection with OpenFile</span></span>

<span data-ttu-id="d9731-117">O exemplo a <xref:System.Windows.Forms.Button> seguir <xref:System.Windows.Forms.Control.Click> usa o manipulador <xref:System.Windows.Forms.OpenFileDialog> de eventos do controle para abrir o com um filtro que mostra apenas arquivos de texto.</span><span class="sxs-lookup"><span data-stu-id="d9731-117">The following example uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open the <xref:System.Windows.Forms.OpenFileDialog> with a filter that shows only text files.</span></span> <span data-ttu-id="d9731-118">Depois que o usuário escolhe um arquivo <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> de texto e seleciona **OK,** o método é usado para abrir o arquivo no Bloco de Notas.</span><span class="sxs-lookup"><span data-stu-id="d9731-118">After the user chooses a text file and selects **OK**, the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is used to open the file in Notepad.</span></span>

 [!code-csharp[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/cs/Form1.cs)]
 [!code-vb[OpenFileDialog#2](~/samples/snippets/winforms/open-files/example2/vb/Form1.vb)]  

## <a name="see-also"></a><span data-ttu-id="d9731-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="d9731-119">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="d9731-120">Componente OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="d9731-120">OpenFileDialog component</span></span>](openfiledialog-component-windows-forms.md)
