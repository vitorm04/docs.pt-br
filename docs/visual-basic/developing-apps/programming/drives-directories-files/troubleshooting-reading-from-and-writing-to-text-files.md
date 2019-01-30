---
title: 'Solução de problemas: lendo e gravando em arquivos de texto (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
ms.openlocfilehash: cc0ec3c624fc4f47a0ef8594669ba120e6628e82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684392"
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a><span data-ttu-id="c093b-102">Solução de problemas: lendo e gravando em arquivos de texto (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c093b-102">Troubleshooting: reading from and writing to text files (Visual Basic)</span></span>
<span data-ttu-id="c093b-103">Este tópico aborda problemas comuns encontrados ao trabalhar com arquivos de texto e sugere uma abordagem para cada um.</span><span class="sxs-lookup"><span data-stu-id="c093b-103">This topic discusses common problems encountered when working with text files and suggests an approach to each.</span></span>  
  
## <a name="common-problems"></a><span data-ttu-id="c093b-104">Problemas comuns</span><span class="sxs-lookup"><span data-stu-id="c093b-104">Common problems</span></span>  
 <span data-ttu-id="c093b-105">Os problemas mais comuns encontrados ao trabalhar com arquivos de texto incluem exceções de segurança, codificações de arquivo ou caminhos inválidos.</span><span class="sxs-lookup"><span data-stu-id="c093b-105">The most common issues encountered when working with text files include security exceptions, file encodings, or invalid paths.</span></span>  
  
### <a name="security-exceptions"></a><span data-ttu-id="c093b-106">Exceções de segurança</span><span class="sxs-lookup"><span data-stu-id="c093b-106">Security exceptions</span></span>  
 <span data-ttu-id="c093b-107">A <xref:System.Security.SecurityException> é lançada quando ocorre um erro de segurança.</span><span class="sxs-lookup"><span data-stu-id="c093b-107">A <xref:System.Security.SecurityException> is thrown when a security error occurs.</span></span> <span data-ttu-id="c093b-108">Isso geralmente é um resultado do usuário não ter as permissões necessárias, o que pode ser resolvido adicionando permissões ou trabalhando com arquivos em um armazenamento isolado.</span><span class="sxs-lookup"><span data-stu-id="c093b-108">This is often a result of the user lacking necessary permissions, which may be solved by adding permissions or working with files in isolated storage.</span></span>  
  
### <a name="file-encodings"></a><span data-ttu-id="c093b-109">Codificações de arquivo</span><span class="sxs-lookup"><span data-stu-id="c093b-109">File encodings</span></span>  
 <span data-ttu-id="c093b-110">As codificações de arquivo, também conhecidas como codificações de caracteres, especificam como representar caracteres no processamento de texto.</span><span class="sxs-lookup"><span data-stu-id="c093b-110">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="c093b-111">Caracteres inesperados em um arquivo de texto podem resultar de uma codificação incorreta.</span><span class="sxs-lookup"><span data-stu-id="c093b-111">Unexpected characters in a text file may result from incorrect encoding.</span></span> <span data-ttu-id="c093b-112">Para a maioria dos arquivos, uma codificação pode ser preferível em relação a outra em termos de quais caracteres de idioma podem ou não ser manipulados, embora o Unicode geralmente seja o ideal.</span><span class="sxs-lookup"><span data-stu-id="c093b-112">For most files, one encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span> <span data-ttu-id="c093b-113">Para saber mais, confira [Codificações de arquivo](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) e <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="c093b-113">For more information, see [File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md) and <xref:System.Text.Encoding>.</span></span>  
  
### <a name="incorrect-paths"></a><span data-ttu-id="c093b-114">Caminhos incorretos</span><span class="sxs-lookup"><span data-stu-id="c093b-114">Incorrect paths</span></span>  
 <span data-ttu-id="c093b-115">Durante a análise de caminhos de arquivo, particularmente caminhos relativos, é fácil fornecer os dados errados.</span><span class="sxs-lookup"><span data-stu-id="c093b-115">When parsing file paths, particularly relative paths, it is easy to supply the wrong data.</span></span> <span data-ttu-id="c093b-116">Muitos problemas podem ser corrigidos certificando-se de que está fornecendo o caminho correto.</span><span class="sxs-lookup"><span data-stu-id="c093b-116">Many problems can be corrected by making sure you are supplying the correct path.</span></span> <span data-ttu-id="c093b-117">Para obter mais informações, confira [Como: Analisar caminhos de arquivo](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span><span class="sxs-lookup"><span data-stu-id="c093b-117">For more information, see [How to: Parse File Paths](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c093b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c093b-118">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- [<span data-ttu-id="c093b-119">Leitura de arquivos</span><span class="sxs-lookup"><span data-stu-id="c093b-119">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="c093b-120">Gravando em arquivos</span><span class="sxs-lookup"><span data-stu-id="c093b-120">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
- [<span data-ttu-id="c093b-121">Analisando arquivos de texto com o objeto TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="c093b-121">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
