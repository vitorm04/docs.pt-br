---
title: Configurando classes de criptografia
description: Entenda como os administradores de computadores podem configurar os algoritmos de criptografia e as implementações de algoritmo padrão que o .NET e os aplicativos usam.
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
ms.openlocfilehash: 5262dfca914fd5306297ea9535bcef3d2088d107
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165202"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="bd3e3-103">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="bd3e3-103">Configuring Cryptography Classes</span></span>

<span data-ttu-id="bd3e3-104">O SDK do Windows permite que os administradores de computador configurem os algoritmos de criptografia e as implementações de algoritmo padrão que o .NET Framework e os aplicativos escritos de forma apropriada usam.</span><span class="sxs-lookup"><span data-stu-id="bd3e3-104">The Windows SDK allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="bd3e3-105">Por exemplo, uma empresa que tem sua própria implementação de um algoritmo criptográfico pode tornar essa implementação o padrão em vez da implementação fornecida no SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="bd3e3-105">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="bd3e3-106">Embora os aplicativos gerenciados que usam a criptografia possam sempre optar por ligar explicitamente a uma implementação específica, é recomendável que eles criem objetos criptográficos usando o sistema de configuração de criptografia.</span><span class="sxs-lookup"><span data-stu-id="bd3e3-106">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bd3e3-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="bd3e3-107">In This Section</span></span>  

 [<span data-ttu-id="bd3e3-108">Mapeando nomes de algoritmo para classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="bd3e3-108">Mapping Algorithm Names to Cryptography Classes</span></span>](map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="bd3e3-109">Descreve como mapear um nome de algoritmo para uma classe de criptografia.</span><span class="sxs-lookup"><span data-stu-id="bd3e3-109">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="bd3e3-110">Mapeando identificadores de objeto para algoritmos de criptografia</span><span class="sxs-lookup"><span data-stu-id="bd3e3-110">Mapping Object Identifiers to Cryptography Algorithms</span></span>](map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="bd3e3-111">Descreve como mapear um identificador de objeto para um algoritmo de criptografia.</span><span class="sxs-lookup"><span data-stu-id="bd3e3-111">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bd3e3-112">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="bd3e3-112">Related Sections</span></span>  

 [<span data-ttu-id="bd3e3-113">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="bd3e3-113">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)  
 <span data-ttu-id="bd3e3-114">Fornece uma visão geral dos serviços de criptografia fornecidos pelo SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="bd3e3-114">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="bd3e3-115">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="bd3e3-115">Cryptography Settings Schema</span></span>](./file-schema/cryptography/index.md)  
 <span data-ttu-id="bd3e3-116">Descreve os elementos que mapeiam nomes amigáveis de algoritmo a classes que implementam algoritmos de criptografia.</span><span class="sxs-lookup"><span data-stu-id="bd3e3-116">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
