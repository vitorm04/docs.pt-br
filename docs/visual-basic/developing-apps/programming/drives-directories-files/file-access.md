---
title: Access de arquivo com o Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- file access
- files [Visual Basic], input and output
- file access, Visual Basic
- files [Visual Basic], I/O
- file I/O classes
- data [Visual Basic], accessing from files
- files [Visual Basic], accessing
- file access, using components
- My.Computer.FileSystem object, accessing files
- I/O [Visual Basic]
- sequential access
ms.assetid: 231533bf-d049-4345-befa-3fb78fe6517d
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2aabea79e3c7a6dabf47647c7e27b072738ba363
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="file-access-with-visual-basic"></a><span data-ttu-id="b2efe-102">Access de arquivo com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b2efe-102">File Access with Visual Basic</span></span>
<span data-ttu-id="b2efe-103">O objeto `My.Computer.FileSystem` fornece ferramentas para trabalhar com arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="b2efe-103">The `My.Computer.FileSystem` object provides tools for working with files and folders.</span></span> <span data-ttu-id="b2efe-104">Suas propriedades, métodos e eventos permitem que você crie, copie, mova, investigue e exclua arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="b2efe-104">Its properties, methods, and events allow you to create, copy, move, investigate, and delete files and folders.</span></span> <span data-ttu-id="b2efe-105">`My.Computer.FileSystem` fornece um desempenho melhor do que as funções herdadas (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput` etc.) que são fornecidas pelo Visual Basic para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="b2efe-105">`My.Computer.FileSystem` provides better performance than the legacy functions (`FileOpen`, `FileClose`, `Input`, `InputString`, `LineInput`, etc.) that are provided by Visual Basic for backward compatibility.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b2efe-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="b2efe-106">In This Section</span></span>  
 [<span data-ttu-id="b2efe-107">Leitura de arquivos</span><span class="sxs-lookup"><span data-stu-id="b2efe-107">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 <span data-ttu-id="b2efe-108">Lista os tópicos que lidam com o uso do objeto `My.Computer.FileSystem` para ler arquivos</span><span class="sxs-lookup"><span data-stu-id="b2efe-108">Lists topics dealing with using the `My.Computer.FileSystem` object to read from files</span></span>  
  
 [<span data-ttu-id="b2efe-109">Gravando em arquivos</span><span class="sxs-lookup"><span data-stu-id="b2efe-109">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 <span data-ttu-id="b2efe-110">Lista os tópicos que lidam com o uso do objeto `My.Computer.FileSystem` para gravar em arquivos</span><span class="sxs-lookup"><span data-stu-id="b2efe-110">Lists topics dealing with using the `My.Computer.FileSystem` object to write to files</span></span>  
  
 [<span data-ttu-id="b2efe-111">Criando, excluindo e movendo arquivos e diretórios</span><span class="sxs-lookup"><span data-stu-id="b2efe-111">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)  
 <span data-ttu-id="b2efe-112">Lista os tópicos que lidam com o uso do objeto `My.Computer.FileSystem` para criar, copiar, excluir e mover arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="b2efe-112">Lists topics dealing with using the `My.Computer.FileSystem` object to creating, copying, deleting and moving files and folders.</span></span>  
  
 [<span data-ttu-id="b2efe-113">Analisando arquivos de texto com o objeto TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="b2efe-113">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 <span data-ttu-id="b2efe-114">Discute como usar o `TextFieldReader` para analisar arquivos de texto, como logs.</span><span class="sxs-lookup"><span data-stu-id="b2efe-114">Discusses how to use the `TextFieldReader` to parse text files such as logs.</span></span>  
  
 [<span data-ttu-id="b2efe-115">Codificações de Arquivo</span><span class="sxs-lookup"><span data-stu-id="b2efe-115">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)  
 <span data-ttu-id="b2efe-116">Descreve as codificações de arquivo e seu uso.</span><span class="sxs-lookup"><span data-stu-id="b2efe-116">Describes file encodings and their use.</span></span>  
  
 [<span data-ttu-id="b2efe-117">Passo a passo: manipulando arquivos e diretórios no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b2efe-117">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="b2efe-118">Demonstra como criar um utilitário que relata informações sobre arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="b2efe-118">Demonstrates how to create a utility that reports information about files and folders.</span></span>  
  
 [<span data-ttu-id="b2efe-119">Solução de problemas: lendo e gravando em arquivos de texto</span><span class="sxs-lookup"><span data-stu-id="b2efe-119">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 <span data-ttu-id="b2efe-120">Lista problemas comuns encontrados ao ler e gravar em arquivos de texto e sugere soluções para cada um.</span><span class="sxs-lookup"><span data-stu-id="b2efe-120">Lists common problems encountered when reading and writing to text files, and suggests remedies for each.</span></span>
