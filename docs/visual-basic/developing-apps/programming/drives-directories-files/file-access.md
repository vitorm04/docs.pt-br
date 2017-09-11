---
title: Access de arquivo com o Visual Basic
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- file access
- files, input and output
- file access, Visual Basic
- files, I/O
- file I/O classes
- data [Visual Basic], accessing from files
- files, accessing
- file access, using components
- My.Computer.FileSystem object, accessing files
- I/O [Visual Basic]
- sequential access
ms.assetid: 231533bf-d049-4345-befa-3fb78fe6517d
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 71e941bf33c3b1051c22c8170b327df9fae7d4b9
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="ee4cb-102">Access de arquivo com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ee4cb-102">File Access with Visual Basic</span></span>
<span data-ttu-id="ee4cb-103">O objeto `My.Computer.FileSystem` fornece ferramentas para trabalhar com arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="ee4cb-103">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="ee4cb-104">Suas propriedades, métodos e eventos permitem que você crie, copie, mova, investigue e exclua arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="ee4cb-104">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="ee4cb-105">`My.Computer.FileSystem` fornece um desempenho melhor do que as funções herdadas (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput` etc.) que são fornecidas pelo [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="ee4cb-105">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ee4cb-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ee4cb-106">In This Section</span></span>  
 [<span data-ttu-id="ee4cb-107">Leitura de arquivos</span><span class="sxs-lookup"><span data-stu-id="ee4cb-107">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 <span data-ttu-id="ee4cb-108">Lista os tópicos que lidam com o uso do objeto `My.Computer.FileSystem` para ler arquivos</span><span class="sxs-lookup"><span data-stu-id="ee4cb-108">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="ee4cb-109">Gravando em arquivos</span><span class="sxs-lookup"><span data-stu-id="ee4cb-109">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 <span data-ttu-id="ee4cb-110">Lista os tópicos que lidam com o uso do objeto `My.Computer.FileSystem` para gravar em arquivos</span><span class="sxs-lookup"><span data-stu-id="ee4cb-110">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="ee4cb-111">Criando, excluindo e movendo arquivos e diretórios</span><span class="sxs-lookup"><span data-stu-id="ee4cb-111">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="ee4cb-112">Lista os tópicos que lidam com o uso do objeto `My.Computer.FileSystem` para criar, copiar, excluir e mover arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="ee4cb-112">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="ee4cb-113">Analisando arquivos de texto com o objeto TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="ee4cb-113">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="ee4cb-114">Discute como usar o `TextFieldReader` para analisar arquivos de texto, como logs.</span><span class="sxs-lookup"><span data-stu-id="ee4cb-114">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="ee4cb-115">Codificações de Arquivo</span><span class="sxs-lookup"><span data-stu-id="ee4cb-115">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 <span data-ttu-id="ee4cb-116">Descreve as codificações de arquivo e seu uso.</span><span class="sxs-lookup"><span data-stu-id="ee4cb-116">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="ee4cb-117">Passo a passo: manipulando arquivos e diretórios no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ee4cb-117">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="ee4cb-118">Demonstra como criar um utilitário que relata informações sobre arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="ee4cb-118">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="ee4cb-119">Solução de problemas: lendo e gravando em arquivos de texto</span><span class="sxs-lookup"><span data-stu-id="ee4cb-119">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="ee4cb-120">Lista problemas comuns encontrados ao ler e gravar em arquivos de texto e sugere soluções para cada um.</span><span class="sxs-lookup"><span data-stu-id="ee4cb-120">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>

