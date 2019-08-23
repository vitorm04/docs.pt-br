---
title: Configurando classes de criptografia
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
ms.openlocfilehash: e53f4c5c9e24fb25b43b7f27b80ab984214eeac2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927767"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="c9937-102">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="c9937-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="c9937-103">O SDK do Windows permite que os administradores de computador configurem os algoritmos de criptografia e as implementações de algoritmo padrão que o .NET Framework e os aplicativos escritos de forma apropriada usam.</span><span class="sxs-lookup"><span data-stu-id="c9937-103">The Windows SDK allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="c9937-104">Por exemplo, uma empresa que tem sua própria implementação de um algoritmo criptográfico pode tornar essa implementação o padrão em vez da implementação fornecida no SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="c9937-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="c9937-105">Embora os aplicativos gerenciados que usam a criptografia possam sempre optar por ligar explicitamente a uma implementação específica, é recomendável que eles criem objetos criptográficos usando o sistema de configuração de criptografia.</span><span class="sxs-lookup"><span data-stu-id="c9937-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c9937-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="c9937-106">In This Section</span></span>  
 [<span data-ttu-id="c9937-107">Mapeando nomes de algoritmo para classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="c9937-107">Mapping Algorithm Names to Cryptography Classes</span></span>](map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="c9937-108">Descreve como mapear um nome de algoritmo para uma classe de criptografia.</span><span class="sxs-lookup"><span data-stu-id="c9937-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="c9937-109">Mapeando identificadores de objeto para algoritmos de criptografia</span><span class="sxs-lookup"><span data-stu-id="c9937-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="c9937-110">Descreve como mapear um identificador de objeto para um algoritmo de criptografia.</span><span class="sxs-lookup"><span data-stu-id="c9937-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c9937-111">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="c9937-111">Related Sections</span></span>  
 [<span data-ttu-id="c9937-112">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="c9937-112">Cryptographic Services</span></span>](../../standard/security/cryptographic-services.md)  
 <span data-ttu-id="c9937-113">Fornece uma visão geral dos serviços de criptografia fornecidos pelo SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="c9937-113">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="c9937-114">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="c9937-114">Cryptography Settings Schema</span></span>](./file-schema/cryptography/index.md)  
 <span data-ttu-id="c9937-115">Descreve os elementos que mapeiam nomes amigáveis de algoritmo a classes que implementam algoritmos de criptografia.</span><span class="sxs-lookup"><span data-stu-id="c9937-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
