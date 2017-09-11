---
title: "Como converter RTF em texto sem formatação (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], converting from RTF
ms.assetid: 3b386a87-899d-4d98-bc82-a980526ddaac
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9e4c7b48467f3b260526c604fa3a36fc5d80374e
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-rtf-to-plain-text-c-programming-guide"></a><span data-ttu-id="cf295-102">Como converter RTF em texto sem formatação (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="cf295-102">How to: Convert RTF to Plain Text (C# Programming Guide)</span></span>
<span data-ttu-id="cf295-103">O Formato Rich Text (RTF) é um formato de documento desenvolvido pela Microsoft no final dos anos 1980 para habilitar a troca de documentos entre sistemas operacionais.</span><span class="sxs-lookup"><span data-stu-id="cf295-103">Rich Text Format (RTF) is a document format developed by Microsoft in the late 1980s to enable the exchange of documents across operating systems.</span></span> <span data-ttu-id="cf295-104">O Microsoft Word e o WordPad podem ler e gravar documentos RTF.</span><span class="sxs-lookup"><span data-stu-id="cf295-104">Both Microsoft Word and WordPad can read and write RTF documents.</span></span> <span data-ttu-id="cf295-105">No .NET Framework, é possível usar o controle <xref:System.Windows.Forms.RichTextBox> para criar um processador de texto que dá suporte ao RTF e habilite um usuário a aplicar formatação ao texto da forma WYSIWIG.</span><span class="sxs-lookup"><span data-stu-id="cf295-105">In the .NET Framework, you can use the <xref:System.Windows.Forms.RichTextBox> control to create a word processor that supports RTF and enables a user to apply formatting to text in a WYSIWIG manner.</span></span>  
  
 <span data-ttu-id="cf295-106">Também é possível utilizar o controle <xref:System.Windows.Forms.RichTextBox> para remover programaticamente os códigos de formatação RTF de um documento e convertê-lo em texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="cf295-106">You can also use the <xref:System.Windows.Forms.RichTextBox> control to programmatically remove the RTF formatting codes from a document and convert it to plain text.</span></span> <span data-ttu-id="cf295-107">Não é necessário inserir o controle em um formulário do Windows para executar esse tipo de operação.</span><span class="sxs-lookup"><span data-stu-id="cf295-107">You do not need to embed the control in a Windows Form to perform this kind of operation.</span></span>  
  
### <a name="to-use-the-richtextbox-control-in-a-project"></a><span data-ttu-id="cf295-108">Para usar o controle RichTextBox em um projeto</span><span class="sxs-lookup"><span data-stu-id="cf295-108">To use the RichTextBox control in a project</span></span>  
  
1.  <span data-ttu-id="cf295-109">Adicionar uma referência para System.Windows.Forms.dll.</span><span class="sxs-lookup"><span data-stu-id="cf295-109">Add a reference to System.Windows.Forms.dll.</span></span>  
  
2.  <span data-ttu-id="cf295-110">Adicione uma diretiva de uso para o namespace `System.Windows.Forms` (opcional).</span><span class="sxs-lookup"><span data-stu-id="cf295-110">Add a using directive for the `System.Windows.Forms` namespace (optional).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf295-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cf295-111">Example</span></span>  
 <span data-ttu-id="cf295-112">O exemplo a seguir converte um arquivo RTF de exemplo para texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="cf295-112">The following example converts a sample RTF file to plain text.</span></span> <span data-ttu-id="cf295-113">O arquivo contém a formatação RTF (como informações de fonte), quatro caracteres Unicode e quatro caracteres ASCII estendidos.</span><span class="sxs-lookup"><span data-stu-id="cf295-113">The file contains RTF formatting (such as font information), four Unicode characters, and four extended ASCII characters.</span></span> <span data-ttu-id="cf295-114">O código de exemplo abre o arquivo, passa seu conteúdo para um <xref:System.Windows.Forms.RichTextBox> como RTF, recupera o conteúdo como texto, exibe o texto em um <xref:System.Windows.Forms.MessageBox> e gera um arquivo em formato UTF-8 com o texto.</span><span class="sxs-lookup"><span data-stu-id="cf295-114">The example code opens the file, passes its content to a <xref:System.Windows.Forms.RichTextBox> as RTF, retrieves the content as text, displays the text in a <xref:System.Windows.Forms.MessageBox>, and outputs the text to a file in UTF-8 format.</span></span>  
  
 <span data-ttu-id="cf295-115">O `MessageBox` e o arquivo de saída contêm o seguinte texto:</span><span class="sxs-lookup"><span data-stu-id="cf295-115">The `MessageBox` and the output file contain the following text:</span></span>  
  
```  
The Greek word for "psyche" is spelled ψυχή. The Greek letters are encoded in Unicode.  
These characters are from the extended ASCII character set (Windows code page 1252):  âäӑå  
```  
  
 <span data-ttu-id="cf295-116">[!code-cs[csProgGuideStrings#33](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-rtf-to-plain-text_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="cf295-116">[!code-cs[csProgGuideStrings#33](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-rtf-to-plain-text_1.cs)]</span></span>  
  
 <span data-ttu-id="cf295-117">Caracteres RTF são codificados em oito bits.</span><span class="sxs-lookup"><span data-stu-id="cf295-117">RTF characters are encoded in eight bits.</span></span> <span data-ttu-id="cf295-118">No entanto, os usuários podem especificar caracteres Unicode, além de caracteres ASCII de páginas de código especificadas.</span><span class="sxs-lookup"><span data-stu-id="cf295-118">However, users can specify Unicode characters in addition to extended ASCII characters from specified code pages.</span></span> <span data-ttu-id="cf295-119">Já que a propriedade <xref:System.Windows.Forms.RichTextBox.Text%2A?displayProperty=fullName> é do tipo [cadeia de caracteres](../../../csharp/language-reference/keywords/string.md), os caracteres são codificados como Unicode UTF-16.</span><span class="sxs-lookup"><span data-stu-id="cf295-119">Because the <xref:System.Windows.Forms.RichTextBox.Text%2A?displayProperty=fullName> property is of type [string](../../../csharp/language-reference/keywords/string.md), the characters are encoded as Unicode UTF-16.</span></span> <span data-ttu-id="cf295-120">Quaisquer caracteres ASCII estendidos e Unicode do documento RTF de origem serão codificados corretamente na saída de texto.</span><span class="sxs-lookup"><span data-stu-id="cf295-120">Any extended ASCII characters and Unicode characters from the source RTF document are correctly encoded in the text output.</span></span>  
  
 <span data-ttu-id="cf295-121">Ao usar o método <xref:System.IO.File.WriteAllText%2A?displayProperty=fullName> para gravar o texto no disco, o texto será codificado como UTF-8 (sem uma marca de ordem de byte).</span><span class="sxs-lookup"><span data-stu-id="cf295-121">If you use the <xref:System.IO.File.WriteAllText%2A?displayProperty=fullName> method to write the text to disk, the text will be encoded as UTF-8 (without a Byte Order Mark).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf295-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf295-122">See Also</span></span>  
 <span data-ttu-id="cf295-123"><xref:System.Windows.Forms.RichTextBox?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="cf295-123"><xref:System.Windows.Forms.RichTextBox?displayProperty=fullName></span></span>   
 [<span data-ttu-id="cf295-124">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="cf295-124">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)

