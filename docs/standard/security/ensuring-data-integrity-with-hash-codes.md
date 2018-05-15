---
title: Assegurando a integridade dos dados com códigos hash
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generating hash
- verifying hash codes
- cryptography [.NET Framework], hash
- data integrity
- checking hash codes
- encryption [.NET Framework], hash
- hash
ms.assetid: 33660f33-b70f-4dca-8c87-ab35cfc2961a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27e4abcd5e8dfe253ba8a7ea1ba5022561ed9ae7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ensuring-data-integrity-with-hash-codes"></a><span data-ttu-id="96e75-102">Assegurando a integridade dos dados com códigos hash</span><span class="sxs-lookup"><span data-stu-id="96e75-102">Ensuring Data Integrity with Hash Codes</span></span>
<span data-ttu-id="96e75-103">Um valor de hash é um valor numérico de comprimento fixo que identifica exclusivamente a dados.</span><span class="sxs-lookup"><span data-stu-id="96e75-103">A hash value is a numeric value of a fixed length that uniquely identifies data.</span></span> <span data-ttu-id="96e75-104">Valores de hash representam grandes quantidades de dados como valores numéricos muito menores, para que eles são usados com assinaturas digitais.</span><span class="sxs-lookup"><span data-stu-id="96e75-104">Hash values represent large amounts of data as much smaller numeric values, so they are used with digital signatures.</span></span> <span data-ttu-id="96e75-105">Você pode assinar um valor de hash de forma mais eficiente que o maior valor de assinatura.</span><span class="sxs-lookup"><span data-stu-id="96e75-105">You can sign a hash value more efficiently than signing the larger value.</span></span> <span data-ttu-id="96e75-106">Valores de hash também são úteis para verificar a integridade dos dados enviados por meio de canais inseguras.</span><span class="sxs-lookup"><span data-stu-id="96e75-106">Hash values are also useful for verifying the integrity of data sent through insecure channels.</span></span> <span data-ttu-id="96e75-107">O valor de hash de dados recebidos pode ser comparado com o valor de hash de dados como ele foi enviado para determinar se os dados foi alterados.</span><span class="sxs-lookup"><span data-stu-id="96e75-107">The hash value of received data can be compared to the hash value of data as it was sent to determine whether the data was altered.</span></span>  
  
 <span data-ttu-id="96e75-108">Este tópico descreve como gerar e verificar códigos hash usando as classes de <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="96e75-108">This topic describes how to generate and verify hash codes by using the classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="generating-a-hash"></a><span data-ttu-id="96e75-109">Gerando um Hash</span><span class="sxs-lookup"><span data-stu-id="96e75-109">Generating a Hash</span></span>  
 <span data-ttu-id="96e75-110">As classes de hash gerenciado podem hash de uma matriz de bytes ou um objeto de fluxo gerenciados.</span><span class="sxs-lookup"><span data-stu-id="96e75-110">The managed hash classes can hash either an array of bytes or a managed stream object.</span></span> <span data-ttu-id="96e75-111">O exemplo a seguir usa o algoritmo de hash SHA1 para criar um valor de hash para uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="96e75-111">The following example uses the SHA1 hash algorithm to create a hash value for a string.</span></span> <span data-ttu-id="96e75-112">O exemplo usa o <xref:System.Text.UnicodeEncoding> classe para converter a cadeia de caracteres em uma matriz de bytes que são transformadas em hash usando o <xref:System.Security.Cryptography.SHA1Managed> classe.</span><span class="sxs-lookup"><span data-stu-id="96e75-112">The example uses the <xref:System.Text.UnicodeEncoding> class to convert the string into an array of bytes that are hashed by using the <xref:System.Security.Cryptography.SHA1Managed> class.</span></span> <span data-ttu-id="96e75-113">O valor de hash é exibido no console.</span><span class="sxs-lookup"><span data-stu-id="96e75-113">The hash value is then displayed to the console.</span></span>  
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="96e75-114">Esse código exibirá a seguinte cadeia de caracteres para o console:</span><span class="sxs-lookup"><span data-stu-id="96e75-114">This code will display the following string to the console:</span></span>  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a><span data-ttu-id="96e75-115">Verificando um Hash</span><span class="sxs-lookup"><span data-stu-id="96e75-115">Verifying a Hash</span></span>  
 <span data-ttu-id="96e75-116">Dados podem ser comparados com um valor de hash para determinar sua integridade.</span><span class="sxs-lookup"><span data-stu-id="96e75-116">Data can be compared to a hash value to determine its integrity.</span></span> <span data-ttu-id="96e75-117">Geralmente, dados é transformado em hash em uma determinada hora e o valor de hash é protegido de alguma forma.</span><span class="sxs-lookup"><span data-stu-id="96e75-117">Usually, data is hashed at a certain time and the hash value is protected in some way.</span></span> <span data-ttu-id="96e75-118">Em um momento posterior, os dados podem ser misturados novamente e comparados com o valor protegido.</span><span class="sxs-lookup"><span data-stu-id="96e75-118">At a later time, the data can be hashed again and compared to the protected value.</span></span> <span data-ttu-id="96e75-119">Se os valores de hash coincidirem, os dados não foi alterados.</span><span class="sxs-lookup"><span data-stu-id="96e75-119">If the hash values match, the data has not been altered.</span></span> <span data-ttu-id="96e75-120">Se os valores não coincidirem, os dados foi corrompidos.</span><span class="sxs-lookup"><span data-stu-id="96e75-120">If the values do not match, the data has been corrupted.</span></span> <span data-ttu-id="96e75-121">Para este sistema de trabalho, o hash protegido deve ser criptografado ou mantido em segredo de todas as partes não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="96e75-121">For this system to work, the protected hash must be encrypted or kept secret from all untrusted parties.</span></span>  
  
 <span data-ttu-id="96e75-122">O exemplo a seguir compara o valor de hash anterior de uma cadeia de caracteres para um novo valor de hash.</span><span class="sxs-lookup"><span data-stu-id="96e75-122">The following example compares the previous hash value of a string to a new hash value.</span></span> <span data-ttu-id="96e75-123">Este exemplo executa um loop em cada byte de valores de hash e faz uma comparação.</span><span class="sxs-lookup"><span data-stu-id="96e75-123">This example loops through each byte of the hash values and makes a comparison.</span></span>  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="96e75-124">Se os dois valores de hash coincidirem, este código exibe o seguinte no console:</span><span class="sxs-lookup"><span data-stu-id="96e75-124">If the two hash values match, this code displays the following to the console:</span></span>  
  
```  
The hash codes match.  
```  
  
 <span data-ttu-id="96e75-125">Se eles não coincidirem, o código exibe o seguinte:</span><span class="sxs-lookup"><span data-stu-id="96e75-125">If they do not match, the code displays the following:</span></span>  
  
```  
The hash codes do not match.  
```  
  
## <a name="see-also"></a><span data-ttu-id="96e75-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96e75-126">See Also</span></span>  
 [<span data-ttu-id="96e75-127">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="96e75-127">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
