---
title: Classes usadas em E/S de arquivo do .NET Framework e o sistema de arquivos (Visual Basic)
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
- file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
caps.latest.revision: 15
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
ms.openlocfilehash: a87d2e6f87b92b5f66706095d3f485c080008e0f
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="classes-used-in-net-framework-file-io-and-the-file-system-visual-basic"></a><span data-ttu-id="9bfaf-102">Classes usadas em E/S de arquivo do .NET Framework e o sistema de arquivos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bfaf-102">Classes Used in .NET Framework File I/O and the File System (Visual Basic)</span></span>
<span data-ttu-id="9bfaf-103">As tabelas a seguir listam as classes usadas comumente para E/S de arquivos do .NET Framework, categorizadas em classes de E/S de arquivos, classes usadas para criar fluxos e classes usadas para ler e gravar em fluxos.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-103">The following tables list the classes commonly used for .NET Framework file I/O, categorized into file I/O classes, classes used for creating streams, and classes used to read and write to streams.</span></span>  
  
 <span data-ttu-id="9bfaf-104">Para inserir a documentação [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] e encontrar uma listagem mais abrangente, consulte [Visão geral da biblioteca de classes](https://msdn.microsoft.com/library/hfa3fa08).</span><span class="sxs-lookup"><span data-stu-id="9bfaf-104">To enter the [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] documentation and find a more comprehensive listing, see [Class Library Overview](https://msdn.microsoft.com/library/hfa3fa08).</span></span>  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a><span data-ttu-id="9bfaf-105">Classes básicas de E/S para arquivos, unidades e pastas</span><span class="sxs-lookup"><span data-stu-id="9bfaf-105">Basic I/O Classes for Files, Drives, and Directories</span></span>  
 <span data-ttu-id="9bfaf-106">A tabela a seguir lista e descreve as principais classes usadas para E/S de arquivos.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-106">The following table lists and describes the main classes used for file I/O.</span></span>  
  
|<span data-ttu-id="9bfaf-107">Classe</span><span class="sxs-lookup"><span data-stu-id="9bfaf-107">Class</span></span>|<span data-ttu-id="9bfaf-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bfaf-108">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=fullName>|<span data-ttu-id="9bfaf-109">Fornece métodos estáticos para criar, mover e enumerar ao longo de diretórios e subdiretórios.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-109">Provides static methods for creating, moving, and enumerating through directories and subdirectories.</span></span>|  
|<xref:System.IO.DirectoryInfo?displayProperty=fullName>|<span data-ttu-id="9bfaf-110">Fornece métodos de instância para criar, mover e enumerar ao longo de diretórios e subdiretórios.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-110">Provides instance methods for creating, moving, and enumerating through directories and subdirectories.</span></span>|  
|<xref:System.IO.DriveInfo?displayProperty=fullName>|<span data-ttu-id="9bfaf-111">Fornece métodos de instância para criar, mover e enumerar ao longo de unidades.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-111">Provides instance methods for creating, moving, and enumerating through drives.</span></span>|  
|<xref:System.IO.File?displayProperty=fullName>|<span data-ttu-id="9bfaf-112">Fornece métodos estáticos para criar, copiar, excluir, mover e abrir arquivos, além de ajudar na criação de um `FileStream`.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-112">Provides static methods for creating, copying, deleting, moving, and opening files, and aids in the creation of a `FileStream`.</span></span>|  
|<xref:System.IO.FileAccess?displayProperty=fullName>|<span data-ttu-id="9bfaf-113">Define constantes para acesso de leitura, gravação ou leitura/gravação para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-113">Defines constants for read, write, or read/write access to a file.</span></span>|  
|<xref:System.IO.FileAttributes?displayProperty=fullName>|<span data-ttu-id="9bfaf-114">Fornece atributos para arquivos e diretórios como `Archive`, `Hidden` e `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-114">Provides attributes for files and directories such as `Archive`, `Hidden`, and `ReadOnly`.</span></span>|  
|<xref:System.IO.FileInfo?displayProperty=fullName>|<span data-ttu-id="9bfaf-115">Fornece métodos estáticos para criar, copiar, excluir, mover e abrir arquivos, além de ajudar na criação de um `FileStream`.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-115">Provides static methods for creating, copying, deleting, moving, and opening files, and aids in the creation of a `FileStream`.</span></span>|  
|<xref:System.IO.FileMode?displayProperty=fullName>|<span data-ttu-id="9bfaf-116">Controla como um arquivo é aberto.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-116">Controls how a file is opened.</span></span> <span data-ttu-id="9bfaf-117">Este parâmetro é especificado em muitos dos construtores para `FileStream` e `IsolatedStorageFileStream`, também para os métodos `Open` de <xref:System.IO.File> e <xref:System.IO.FileInfo>.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-117">This parameter is specified in many of the constructors for `FileStream` and `IsolatedStorageFileStream`, and for the `Open` methods of <xref:System.IO.File> and <xref:System.IO.FileInfo>.</span></span>|  
|<xref:System.IO.FileShare?displayProperty=fullName>|<span data-ttu-id="9bfaf-118">Define constantes para controlar o tipo de acesso que outros fluxos de arquivos podem ter ao mesmo arquivo.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-118">Defines constants for controlling the type of access other file streams can have to the same file.</span></span>|  
|<xref:System.IO.Path?displayProperty=fullName>|<span data-ttu-id="9bfaf-119">Fornece métodos e propriedades para processar cadeias de caracteres de diretório.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-119">Provides methods and properties for processing directory strings.</span></span>|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName>|<span data-ttu-id="9bfaf-120">Controla o acesso de arquivos e pastas definindo permissões <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> e <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A>.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-120">Controls the access of files and folders by defining <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> and <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> permissions.</span></span>|  
  
## <a name="classes-used-to-create-streams"></a><span data-ttu-id="9bfaf-121">Classes usadas para criar fluxos</span><span class="sxs-lookup"><span data-stu-id="9bfaf-121">Classes Used to Create Streams</span></span>  
 <span data-ttu-id="9bfaf-122">A tabela a seguir lista e descreve as principais classes usadas para criar fluxos.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-122">The following table lists and describes the main classes used to create streams.</span></span>  
  
|<span data-ttu-id="9bfaf-123">Classe</span><span class="sxs-lookup"><span data-stu-id="9bfaf-123">Class</span></span>|<span data-ttu-id="9bfaf-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bfaf-124">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=fullName>|<span data-ttu-id="9bfaf-125">Adiciona uma camada de armazenamento em buffer para ler e gravar operações em outro fluxo.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-125">Adds a buffering layer to read and write operations on another stream.</span></span>|  
|<xref:System.IO.FileStream?displayProperty=fullName>|<span data-ttu-id="9bfaf-126">Dá suporte ao acesso aleatório a arquivos por meio de seu método <xref:System.IO.FileStream.Seek%2A>.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-126">Supports random access to files through its <xref:System.IO.FileStream.Seek%2A> method.</span></span> <span data-ttu-id="9bfaf-127"><xref:System.IO.FileStream> abre arquivos de forma síncrona por padrão, mas também dá suporte à operação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-127"><xref:System.IO.FileStream> opens files synchronously by default but also supports asynchronous operation.</span></span>|  
|<xref:System.IO.MemoryStream?displayProperty=fullName>|<span data-ttu-id="9bfaf-128">Cria um fluxo cujo repositório de backup é a memória, em vez de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-128">Creates a stream whose backing store is memory, rather than a file.</span></span>|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=fullName>|<span data-ttu-id="9bfaf-129">Fornece o fluxo de dados subjacente para acesso à rede.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-129">Provides the underlying stream of data for network access.</span></span>|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=fullName>|<span data-ttu-id="9bfaf-130">Define uma transmissão que liga fluxos de dados a transformações criptográficas.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-130">Defines a stream that links data streams to cryptographic transformations.</span></span>|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a><span data-ttu-id="9bfaf-131">Classes usadas para ler e gravar em fluxos</span><span class="sxs-lookup"><span data-stu-id="9bfaf-131">Classes Used to Read from and Write to Streams</span></span>  
 <span data-ttu-id="9bfaf-132">A tabela a seguir mostra as classes específicas usadas para ler e gravar em arquivos com fluxos.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-132">The following table shows the specific classes used for reading from and writing to files with streams.</span></span>  
  
|<span data-ttu-id="9bfaf-133">**Class**</span><span class="sxs-lookup"><span data-stu-id="9bfaf-133">**Class**</span></span>|<span data-ttu-id="9bfaf-134">**Descrição**</span><span class="sxs-lookup"><span data-stu-id="9bfaf-134">**Description**</span></span>|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=fullName>|<span data-ttu-id="9bfaf-135">Lê cadeias de caracteres codificadas e tipos de dados primitivos de um <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-135">Reads encoded strings and primitive data types from a <xref:System.IO.FileStream>.</span></span>|  
|<xref:System.IO.BinaryWriter?displayProperty=fullName>|<span data-ttu-id="9bfaf-136">Grava cadeias de caracteres codificadas e tipos de dados primitivos em um <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-136">Writes encoded strings and primitive data types to a <xref:System.IO.FileStream>.</span></span>|  
|<xref:System.IO.StreamReader?displayProperty=fullName>|<span data-ttu-id="9bfaf-137">Lê caracteres de um <xref:System.IO.FileStream>, usando <xref:System.IO.StreamReader.CurrentEncoding%2A> para converter caracteres em bytes e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-137">Reads characters from a <xref:System.IO.FileStream>, using <xref:System.IO.StreamReader.CurrentEncoding%2A> to convert characters to and from bytes.</span></span> <span data-ttu-id="9bfaf-138"><xref:System.IO.StreamReader> tem um construtor que tenta determinar o <xref:System.IO.StreamReader.CurrentEncoding%2A> correto de determinado fluxo, com base na presença de um preâmbulo específico de <xref:System.IO.StreamReader.CurrentEncoding%2A>, como uma marca de ordem de byte.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-138"><xref:System.IO.StreamReader> has a constructor that attempts to ascertain the correct <xref:System.IO.StreamReader.CurrentEncoding%2A> for a given stream, based on the presence of a <xref:System.IO.StreamReader.CurrentEncoding%2A>-specific preamble, such as a byte order mark.</span></span>|  
|<xref:System.IO.StreamWriter?displayProperty=fullName>|<span data-ttu-id="9bfaf-139">Grava caracteres em um `FileStream`, usando <xref:System.IO.StreamWriter.Encoding%2A> para converter caracteres em bytes.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-139">Writes characters to a `FileStream`, using <xref:System.IO.StreamWriter.Encoding%2A> to convert characters to bytes.</span></span>|  
|<xref:System.IO.StringReader?displayProperty=fullName>|<span data-ttu-id="9bfaf-140">Lê caracteres de um `String`.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-140">Reads characters from a `String`.</span></span> <span data-ttu-id="9bfaf-141">A saída pode ser um fluxo em qualquer codificação ou um `String`.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-141">Output can be either a stream in any encoding or a `String`.</span></span>|  
|<xref:System.IO.StringWriter?displayProperty=fullName>|<span data-ttu-id="9bfaf-142">Grava caracteres em um `String`.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-142">Writes characters to a `String`.</span></span> <span data-ttu-id="9bfaf-143">A saída pode ser um fluxo em qualquer codificação ou um `String`.</span><span class="sxs-lookup"><span data-stu-id="9bfaf-143">Output can be either a stream in any encoding or a `String`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9bfaf-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bfaf-144">See Also</span></span>  
 <span data-ttu-id="9bfaf-145">[Compondo fluxos](https://msdn.microsoft.com/library/e4y2dch9) </span><span class="sxs-lookup"><span data-stu-id="9bfaf-145">[Composing Streams](https://msdn.microsoft.com/library/e4y2dch9) </span></span>  
 <span data-ttu-id="9bfaf-146">[E/S de arquivo e de fluxo](https://msdn.microsoft.com/library/k3352a4t) </span><span class="sxs-lookup"><span data-stu-id="9bfaf-146">[File and Stream I/O](https://msdn.microsoft.com/library/k3352a4t) </span></span>  
 <span data-ttu-id="9bfaf-147">[E/S de arquivo assíncrona](https://msdn.microsoft.com/library/kztecsys) </span><span class="sxs-lookup"><span data-stu-id="9bfaf-147">[Asynchronous File I/O](https://msdn.microsoft.com/library/kztecsys) </span></span>  
 [<span data-ttu-id="9bfaf-148">Noções básicas de E/S de arquivo do .NET Framework e o sistema de arquivos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bfaf-148">Basics of .NET Framework File I/O and the File System (Visual Basic)</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)

