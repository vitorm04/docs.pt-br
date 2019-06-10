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
ms.openlocfilehash: b5c1178519601d7dcb7c5b3014f413b6436746fb
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816165"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="647b7-102">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="647b7-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="647b7-103">O [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] permite que os administradores do computador configurar os algoritmos de criptografia padrão e implementações de algoritmo que usam o .NET Framework e aplicativos escritos corretamente.</span><span class="sxs-lookup"><span data-stu-id="647b7-103">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="647b7-104">Por exemplo, uma empresa que tem sua própria implementação de um algoritmo de criptografia pode fazer essa implementação padrão em vez da implementação é fornecido no SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="647b7-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the Windows SDK.</span></span> <span data-ttu-id="647b7-105">Embora os aplicativos gerenciados que usam criptografia sempre podem optar por associar explicitamente a uma implementação específica, é recomendável que criar objetos criptográficos usando o sistema de configuração de criptografia.</span><span class="sxs-lookup"><span data-stu-id="647b7-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="647b7-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="647b7-106">In This Section</span></span>  
 [<span data-ttu-id="647b7-107">Mapeando nomes de algoritmo para classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="647b7-107">Mapping Algorithm Names to Cryptography Classes</span></span>](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="647b7-108">Descreve como mapear um nome de algoritmo para uma classe de criptografia.</span><span class="sxs-lookup"><span data-stu-id="647b7-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="647b7-109">Mapeando identificadores de objeto para algoritmos de criptografia</span><span class="sxs-lookup"><span data-stu-id="647b7-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="647b7-110">Descreve como mapear um identificador de objeto para um algoritmo de criptografia.</span><span class="sxs-lookup"><span data-stu-id="647b7-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="647b7-111">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="647b7-111">Related Sections</span></span>  
 [<span data-ttu-id="647b7-112">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="647b7-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 <span data-ttu-id="647b7-113">Fornece uma visão geral dos serviços de criptografia fornecidos pelo SDK do Windows.</span><span class="sxs-lookup"><span data-stu-id="647b7-113">Provides an overview of cryptographic services provided by the Windows SDK.</span></span>  
  
 [<span data-ttu-id="647b7-114">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="647b7-114">Cryptography Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 <span data-ttu-id="647b7-115">Descreve os elementos que mapeiam nomes amigáveis de algoritmo a classes que implementam algoritmos de criptografia.</span><span class="sxs-lookup"><span data-stu-id="647b7-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
