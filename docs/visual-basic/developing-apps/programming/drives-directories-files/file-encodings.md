---
title: "Codificações de arquivo (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: deaab4371ab0d5d15c627bfd6352a7090bf08024
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="file-encodings-visual-basic"></a><span data-ttu-id="079d3-102">Codificações de arquivo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="079d3-102">File Encodings (Visual Basic)</span></span>
<span data-ttu-id="079d3-103">As codificações de arquivo, também conhecidas como codificações de caracteres, especificam como representar caracteres no processamento de texto.</span><span class="sxs-lookup"><span data-stu-id="079d3-103">File encodings, also known as character encodings, specify how to represent characters when text processing.</span></span> <span data-ttu-id="079d3-104">Uma codificação pode ser preferível em relação a outra em termos de quais caracteres de idioma podem ou não ser manipulados, embora o Unicode geralmente seja o ideal.</span><span class="sxs-lookup"><span data-stu-id="079d3-104">One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.</span></span>  
  
 <span data-ttu-id="079d3-105">Durante a leitura ou gravação em arquivos, combinar incorretamente as codificações de arquivo pode resultar em exceções ou resultados incorretos.</span><span class="sxs-lookup"><span data-stu-id="079d3-105">When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.</span></span>  
  
## <a name="types-of-encodings"></a><span data-ttu-id="079d3-106">Tipos de Codificações</span><span class="sxs-lookup"><span data-stu-id="079d3-106">Types of Encodings</span></span>  
 <span data-ttu-id="079d3-107">O Unicode é a codificação preferencial ao trabalhar com arquivos.</span><span class="sxs-lookup"><span data-stu-id="079d3-107">Unicode is the preferred encoding when working with files.</span></span> <span data-ttu-id="079d3-108">O Unicode é um padrão de codificação de caracteres global que usa valores de código de 16 bits para representar todos os caracteres utilizados na computação moderna, incluindo símbolos técnicos e caracteres especiais usados em publicações.</span><span class="sxs-lookup"><span data-stu-id="079d3-108">Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.</span></span>  
  
 <span data-ttu-id="079d3-109">Os padrões de codificação de caracteres anteriores consistiam em conjuntos de caracteres tradicionais, como o conjunto de caracteres ANSI do Windows que usa valores de código de 8 bits ou combinações de valores de 8 bits, a fim de representar os caracteres usados em um idioma ou região geográfica específicos.</span><span class="sxs-lookup"><span data-stu-id="079d3-109">Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.</span></span>  
  
## <a name="encoding-class"></a><span data-ttu-id="079d3-110">Classe de Codificação</span><span class="sxs-lookup"><span data-stu-id="079d3-110">Encoding Class</span></span>  
 <span data-ttu-id="079d3-111">A classe <xref:System.Text.Encoding> representa uma codificação de caracteres.</span><span class="sxs-lookup"><span data-stu-id="079d3-111">The <xref:System.Text.Encoding> class represents a character encoding.</span></span> <span data-ttu-id="079d3-112">Esta tabela lista os tipos de codificações disponíveis e descreve cada uma.</span><span class="sxs-lookup"><span data-stu-id="079d3-112">This table lists the type of encodings available and describes each.</span></span>  
  
|<span data-ttu-id="079d3-113">Nome</span><span class="sxs-lookup"><span data-stu-id="079d3-113">Name</span></span>|<span data-ttu-id="079d3-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="079d3-114">Description</span></span>|
|---|---|    
|<xref:System.Text.ASCIIEncoding>|<span data-ttu-id="079d3-115">Representa uma codificação de caracteres ASCII de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="079d3-115">Represents an ASCII character encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UnicodeEncoding>|<span data-ttu-id="079d3-116">Representa uma codificação de caracteres Unicode UTF-16.</span><span class="sxs-lookup"><span data-stu-id="079d3-116">Represents a UTF-16 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF32Encoding>|<span data-ttu-id="079d3-117">Representa uma codificação de caracteres Unicode UTF-32.</span><span class="sxs-lookup"><span data-stu-id="079d3-117">Represents a UTF-32 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF7Encoding>|<span data-ttu-id="079d3-118">Representa uma codificação de caracteres Unicode UTF-7.</span><span class="sxs-lookup"><span data-stu-id="079d3-118">Represents a UTF-7 encoding of Unicode characters.</span></span>|  
|<xref:System.Text.UTF8Encoding>|<span data-ttu-id="079d3-119">Representa uma codificação de caracteres Unicode UTF-8. </span><span class="sxs-lookup"><span data-stu-id="079d3-119">Represents a UTF-8 encoding of Unicode characters.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="079d3-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="079d3-120">See Also</span></span>  
 [<span data-ttu-id="079d3-121">Leitura de arquivos</span><span class="sxs-lookup"><span data-stu-id="079d3-121">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [<span data-ttu-id="079d3-122">Gravando em arquivos</span><span class="sxs-lookup"><span data-stu-id="079d3-122">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
