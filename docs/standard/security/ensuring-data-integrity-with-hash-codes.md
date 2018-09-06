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
ms.openlocfilehash: 16770ea938973372d1d94c628c42d5d5bf10c695
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43874986"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a><span data-ttu-id="5e60f-102">Assegurando a integridade dos dados com códigos hash</span><span class="sxs-lookup"><span data-stu-id="5e60f-102">Ensuring Data Integrity with Hash Codes</span></span>
<span data-ttu-id="5e60f-103">Um valor de hash é um valor numérico de comprimento fixo que identifica exclusivamente a dados.</span><span class="sxs-lookup"><span data-stu-id="5e60f-103">A hash value is a numeric value of a fixed length that uniquely identifies data.</span></span> <span data-ttu-id="5e60f-104">Valores de hash representam grandes quantidades de dados como valores numéricos muito menores, para que eles são usados com assinaturas digitais.</span><span class="sxs-lookup"><span data-stu-id="5e60f-104">Hash values represent large amounts of data as much smaller numeric values, so they are used with digital signatures.</span></span> <span data-ttu-id="5e60f-105">Você pode assinar um valor de hash de forma mais eficiente que o maior valor de assinatura.</span><span class="sxs-lookup"><span data-stu-id="5e60f-105">You can sign a hash value more efficiently than signing the larger value.</span></span> <span data-ttu-id="5e60f-106">Valores de hash também são úteis para verificar a integridade dos dados enviados por meio de canais inseguros.</span><span class="sxs-lookup"><span data-stu-id="5e60f-106">Hash values are also useful for verifying the integrity of data sent through insecure channels.</span></span> <span data-ttu-id="5e60f-107">O valor de hash dos dados recebidos pode ser comparado com o valor de hash de dados como ele foi enviado para determinar se os dados foi alterados.</span><span class="sxs-lookup"><span data-stu-id="5e60f-107">The hash value of received data can be compared to the hash value of data as it was sent to determine whether the data was altered.</span></span>  
  
 <span data-ttu-id="5e60f-108">Este tópico descreve como gerar e verificar códigos hash usando as classes de <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="5e60f-108">This topic describes how to generate and verify hash codes by using the classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="generating-a-hash"></a><span data-ttu-id="5e60f-109">Gerar um Hash</span><span class="sxs-lookup"><span data-stu-id="5e60f-109">Generating a Hash</span></span>  
 <span data-ttu-id="5e60f-110">As classes de hash gerenciados podem discutir uma matriz de bytes ou um objeto de fluxo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5e60f-110">The managed hash classes can hash either an array of bytes or a managed stream object.</span></span> <span data-ttu-id="5e60f-111">O exemplo a seguir usa o algoritmo de hash SHA1 para criar um valor de hash para uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="5e60f-111">The following example uses the SHA1 hash algorithm to create a hash value for a string.</span></span> <span data-ttu-id="5e60f-112">O exemplo usa o <xref:System.Text.UnicodeEncoding> classe para converter a cadeia de caracteres em uma matriz de bytes que são transformadas em hash usando o <xref:System.Security.Cryptography.SHA1Managed> classe.</span><span class="sxs-lookup"><span data-stu-id="5e60f-112">The example uses the <xref:System.Text.UnicodeEncoding> class to convert the string into an array of bytes that are hashed by using the <xref:System.Security.Cryptography.SHA1Managed> class.</span></span> <span data-ttu-id="5e60f-113">O valor de hash é exibido no console.</span><span class="sxs-lookup"><span data-stu-id="5e60f-113">The hash value is then displayed to the console.</span></span>  
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="5e60f-114">Esse código exibirá a seguinte cadeia de caracteres no console:</span><span class="sxs-lookup"><span data-stu-id="5e60f-114">This code will display the following string to the console:</span></span>  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a><span data-ttu-id="5e60f-115">Verificando um Hash</span><span class="sxs-lookup"><span data-stu-id="5e60f-115">Verifying a Hash</span></span>  
 <span data-ttu-id="5e60f-116">Dados podem ser comparados a um valor de hash para determinar sua integridade.</span><span class="sxs-lookup"><span data-stu-id="5e60f-116">Data can be compared to a hash value to determine its integrity.</span></span> <span data-ttu-id="5e60f-117">Normalmente, os dados é transformado em hash em um determinado momento e o valor de hash é protegido de alguma forma.</span><span class="sxs-lookup"><span data-stu-id="5e60f-117">Usually, data is hashed at a certain time and the hash value is protected in some way.</span></span> <span data-ttu-id="5e60f-118">Em um momento posterior, os dados podem ser transformada em hash novamente e comparado com o valor protegido.</span><span class="sxs-lookup"><span data-stu-id="5e60f-118">At a later time, the data can be hashed again and compared to the protected value.</span></span> <span data-ttu-id="5e60f-119">Se os valores de hash corresponderem, os dados não foram alterados.</span><span class="sxs-lookup"><span data-stu-id="5e60f-119">If the hash values match, the data has not been altered.</span></span> <span data-ttu-id="5e60f-120">Se os valores não corresponderem, os dados foi corrompidos.</span><span class="sxs-lookup"><span data-stu-id="5e60f-120">If the values do not match, the data has been corrupted.</span></span> <span data-ttu-id="5e60f-121">Para este sistema funcione, o hash protegido deve ser criptografado ou mantido em segredo de todas as partes não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="5e60f-121">For this system to work, the protected hash must be encrypted or kept secret from all untrusted parties.</span></span>  
  
 <span data-ttu-id="5e60f-122">O exemplo a seguir compara o valor de hash anterior de uma cadeia de caracteres para um novo valor de hash.</span><span class="sxs-lookup"><span data-stu-id="5e60f-122">The following example compares the previous hash value of a string to a new hash value.</span></span> <span data-ttu-id="5e60f-123">Este exemplo executa um loop em cada byte dos valores de hash e faz uma comparação.</span><span class="sxs-lookup"><span data-stu-id="5e60f-123">This example loops through each byte of the hash values and makes a comparison.</span></span>  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="5e60f-124">Se dois valores de hash corresponderem, esse código exibe o seguinte no console:</span><span class="sxs-lookup"><span data-stu-id="5e60f-124">If the two hash values match, this code displays the following to the console:</span></span>  
  
```  
The hash codes match.  
```  
  
 <span data-ttu-id="5e60f-125">Se eles não corresponderem, o código exibe o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5e60f-125">If they do not match, the code displays the following:</span></span>  
  
```  
The hash codes do not match.  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e60f-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e60f-126">See also</span></span>

- [<span data-ttu-id="5e60f-127">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="5e60f-127">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
