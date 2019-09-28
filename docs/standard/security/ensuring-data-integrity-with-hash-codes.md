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
ms.openlocfilehash: 995f54e81a48fb3f809d99981ad135974544eb28
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353173"
---
# <a name="ensuring-data-integrity-with-hash-codes"></a><span data-ttu-id="f8645-102">Assegurando a integridade dos dados com códigos hash</span><span class="sxs-lookup"><span data-stu-id="f8645-102">Ensuring Data Integrity with Hash Codes</span></span>
<span data-ttu-id="f8645-103">Um valor de hash é um valor numérico de um comprimento fixo que identifica dados exclusivamente.</span><span class="sxs-lookup"><span data-stu-id="f8645-103">A hash value is a numeric value of a fixed length that uniquely identifies data.</span></span> <span data-ttu-id="f8645-104">Os valores de hash representam grandes quantidades de dados como valores numéricos muito menores, para que sejam usados com assinaturas digitais.</span><span class="sxs-lookup"><span data-stu-id="f8645-104">Hash values represent large amounts of data as much smaller numeric values, so they are used with digital signatures.</span></span> <span data-ttu-id="f8645-105">Você pode assinar um valor de hash com mais eficiência do que assinar o valor maior.</span><span class="sxs-lookup"><span data-stu-id="f8645-105">You can sign a hash value more efficiently than signing the larger value.</span></span> <span data-ttu-id="f8645-106">Os valores de hash também são úteis para verificar a integridade dos dados enviados por meio de canais inseguros.</span><span class="sxs-lookup"><span data-stu-id="f8645-106">Hash values are also useful for verifying the integrity of data sent through insecure channels.</span></span> <span data-ttu-id="f8645-107">O valor de hash dos dados recebidos pode ser comparado ao valor de hash dos dados conforme eles foram enviados para determinar se os dados foram alterados.</span><span class="sxs-lookup"><span data-stu-id="f8645-107">The hash value of received data can be compared to the hash value of data as it was sent to determine whether the data was altered.</span></span>  
  
 <span data-ttu-id="f8645-108">Este tópico descreve como gerar e verificar os códigos de hash usando as classes no <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span><span class="sxs-lookup"><span data-stu-id="f8645-108">This topic describes how to generate and verify hash codes by using the classes in the <xref:System.Security.Cryptography?displayProperty=nameWithType> namespace.</span></span>  
  
## <a name="generating-a-hash"></a><span data-ttu-id="f8645-109">Gerando um hash</span><span class="sxs-lookup"><span data-stu-id="f8645-109">Generating a Hash</span></span>  
 <span data-ttu-id="f8645-110">As classes de hash gerenciadas podem aplicar hash a uma matriz de bytes ou a um objeto de fluxo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f8645-110">The managed hash classes can hash either an array of bytes or a managed stream object.</span></span> <span data-ttu-id="f8645-111">O exemplo a seguir usa o algoritmo de hash SHA1 para criar um valor de hash para uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="f8645-111">The following example uses the SHA1 hash algorithm to create a hash value for a string.</span></span> <span data-ttu-id="f8645-112">O exemplo usa a <xref:System.Text.UnicodeEncoding> classe para converter a cadeia de caracteres em uma matriz de bytes com hash usando a <xref:System.Security.Cryptography.SHA1Managed> classe.</span><span class="sxs-lookup"><span data-stu-id="f8645-112">The example uses the <xref:System.Text.UnicodeEncoding> class to convert the string into an array of bytes that are hashed by using the <xref:System.Security.Cryptography.SHA1Managed> class.</span></span> <span data-ttu-id="f8645-113">O valor de hash é exibido para o console.</span><span class="sxs-lookup"><span data-stu-id="f8645-113">The hash value is then displayed to the console.</span></span>  

 <span data-ttu-id="f8645-114">Devido a problemas de colisão com o SHA1, a Microsoft recomenda SHA256 ou melhor.</span><span class="sxs-lookup"><span data-stu-id="f8645-114">Due to collision problems with SHA1, Microsoft recommends SHA256 or better.</span></span>
  
 [!code-csharp[GeneratingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/generatingahash/cs/program.cs#1)]
 [!code-vb[GeneratingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/generatingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="f8645-115">Esse código exibirá a seguinte cadeia de caracteres para o console:</span><span class="sxs-lookup"><span data-stu-id="f8645-115">This code will display the following string to the console:</span></span>  
  
 `59 4 248 102 77 97 142 201 210 12 224 93 25 41 100 197 213 134 130 135`  
  
## <a name="verifying-a-hash"></a><span data-ttu-id="f8645-116">Verificando um hash</span><span class="sxs-lookup"><span data-stu-id="f8645-116">Verifying a Hash</span></span>  
 <span data-ttu-id="f8645-117">Os dados podem ser comparados a um valor de hash para determinar sua integridade.</span><span class="sxs-lookup"><span data-stu-id="f8645-117">Data can be compared to a hash value to determine its integrity.</span></span> <span data-ttu-id="f8645-118">Normalmente, os dados são codificados em hash em um determinado momento e o valor de hash é protegido de alguma forma.</span><span class="sxs-lookup"><span data-stu-id="f8645-118">Usually, data is hashed at a certain time and the hash value is protected in some way.</span></span> <span data-ttu-id="f8645-119">Mais tarde, os dados podem ser codificados novamente e comparados com o valor protegido.</span><span class="sxs-lookup"><span data-stu-id="f8645-119">At a later time, the data can be hashed again and compared to the protected value.</span></span> <span data-ttu-id="f8645-120">Se os valores de hash forem correspondentes, os dados não foram alterados.</span><span class="sxs-lookup"><span data-stu-id="f8645-120">If the hash values match, the data has not been altered.</span></span> <span data-ttu-id="f8645-121">Se os valores não corresponderem, os dados ficarão corrompidos.</span><span class="sxs-lookup"><span data-stu-id="f8645-121">If the values do not match, the data has been corrupted.</span></span> <span data-ttu-id="f8645-122">Para que esse sistema funcione, o hash protegido deve ser criptografado ou mantido em segredo de todas as partes não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="f8645-122">For this system to work, the protected hash must be encrypted or kept secret from all untrusted parties.</span></span>  
  
 <span data-ttu-id="f8645-123">O exemplo a seguir compara o valor de hash anterior de uma cadeia de caracteres com um novo valor de hash.</span><span class="sxs-lookup"><span data-stu-id="f8645-123">The following example compares the previous hash value of a string to a new hash value.</span></span> <span data-ttu-id="f8645-124">Este exemplo percorre cada byte dos valores de hash e faz uma comparação.</span><span class="sxs-lookup"><span data-stu-id="f8645-124">This example loops through each byte of the hash values and makes a comparison.</span></span>  
  
 [!code-csharp[VerifyingAHash#1](../../../samples/snippets/csharp/VS_Snippets_CLR/verifyingahash/cs/program.cs#1)]
 [!code-vb[VerifyingAHash#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/verifyingahash/vb/program.vb#1)]  
  
 <span data-ttu-id="f8645-125">Se os dois valores de hash corresponderem, esse código exibirá o seguinte no console:</span><span class="sxs-lookup"><span data-stu-id="f8645-125">If the two hash values match, this code displays the following to the console:</span></span>  
  
```console  
The hash codes match.  
```  
  
 <span data-ttu-id="f8645-126">Se eles não corresponderem, o código exibirá o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f8645-126">If they do not match, the code displays the following:</span></span>  
  
```console  
The hash codes do not match.  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8645-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8645-127">See also</span></span>

- [<span data-ttu-id="f8645-128">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="f8645-128">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
