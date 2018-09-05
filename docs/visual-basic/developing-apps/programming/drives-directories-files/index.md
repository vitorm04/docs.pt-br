---
title: Processando unidades, diretórios e arquivos (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- drives
- drives, processing
- Visual Basic code, file access
- files [Visual Basic], processing
- files [Visual Basic], accessing
- directories [Visual Studio], processing
ms.assetid: f1db14c8-a4fd-4d0b-8323-c7cb29d688c2
ms.openlocfilehash: 0c9c1c787138595f725316a580acda9c5d4d43a9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43662668"
---
# <a name="processing-drives-directories-and-files-visual-basic"></a><span data-ttu-id="3c533-102">Processando unidades, diretórios e arquivos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c533-102">Processing Drives, Directories, and Files (Visual Basic)</span></span>
<span data-ttu-id="3c533-103">Você pode usar o Visual Basic para processar unidades, pastas e arquivos com o objeto `My.Computer.FileSystem`, que fornece um melhor desempenho e é mais fácil de usar que os métodos tradicionais, como as funções `FileOpen` e `Write` (embora elas ainda estejam disponíveis).</span><span class="sxs-lookup"><span data-stu-id="3c533-103">You can use Visual Basic to process drives, folders, and files with the `My.Computer.FileSystem` object, which provides better performance and is easier to use than traditional methods such as the `FileOpen` and `Write` functions (although they are still available).</span></span> <span data-ttu-id="3c533-104">As seções a seguir discutem esses métodos em detalhes.</span><span class="sxs-lookup"><span data-stu-id="3c533-104">The following sections discuss these methods in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3c533-105">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="3c533-105">In This Section</span></span>  
 [<span data-ttu-id="3c533-106">Access de arquivo com o Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3c533-106">File Access with Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)  
 <span data-ttu-id="3c533-107">Discute como usar o objeto `My.Computer.FileSystem` para trabalhar com arquivos, unidades e pastas.</span><span class="sxs-lookup"><span data-stu-id="3c533-107">Discusses how to use the `My.Computer.FileSystem` object to work with files, drives, and folders.</span></span>  
  
 [<span data-ttu-id="3c533-108">Noções básicas de E/S de arquivo do .NET Framework e o sistema de arquivos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c533-108">Basics of .NET Framework File I/O and the File System (Visual Basic)</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)  
 <span data-ttu-id="3c533-109">Fornece uma visão geral dos conceitos de E/S de arquivo no .NET Framework, incluindo fluxos, armazenamento isolado, eventos de arquivo, atributos de arquivo e acesso a arquivos.</span><span class="sxs-lookup"><span data-stu-id="3c533-109">Provides an overview of file I/O concepts in the .NET Framework, including streams, isolated storage, file events, file attributes, and file access.</span></span>  
  
 [<span data-ttu-id="3c533-110">Instruções passo a passo: manipulando arquivos usando métodos do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3c533-110">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)  
 <span data-ttu-id="3c533-111">Demonstra como usar o [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] para manipular arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="3c533-111">Demonstrates how to use the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] to manipulate files and folders.</span></span>  
  
 [<span data-ttu-id="3c533-112">Passo a passo: manipulando arquivos e diretórios no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3c533-112">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 <span data-ttu-id="3c533-113">Demonstra como usar o objeto `My.Computer.FileSystem` para manipular arquivos e pastas.</span><span class="sxs-lookup"><span data-stu-id="3c533-113">Demonstrates how to use the `My.Computer.FileSystem` object to manipulate files and folders.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3c533-114">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="3c533-114">Related Sections</span></span>  
 [<span data-ttu-id="3c533-115">Estrutura do Programa e Convenções de Código</span><span class="sxs-lookup"><span data-stu-id="3c533-115">Program Structure and Code Conventions</span></span>](../../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 <span data-ttu-id="3c533-116">Fornece diretrizes para a estrutura física e a aparência dos programas.</span><span class="sxs-lookup"><span data-stu-id="3c533-116">Provides guidelines for the physical structure and appearance of programs.</span></span>  
  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <span data-ttu-id="3c533-117">Documentação de referência do objeto `My.Computer.FileSystem` e seus membros.</span><span class="sxs-lookup"><span data-stu-id="3c533-117">Reference documentation for the `My.Computer.FileSystem` object and its members.</span></span>
