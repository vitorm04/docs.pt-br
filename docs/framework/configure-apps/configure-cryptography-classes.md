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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b9153b4525063d6c52e22d754d68ffa42e914d00
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47074895"
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="61f67-102">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="61f67-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="61f67-103">O [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] permite que os administradores do computador configurar os algoritmos de criptografia padrão e implementações de algoritmo que usam o .NET Framework e aplicativos escritos corretamente.</span><span class="sxs-lookup"><span data-stu-id="61f67-103">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="61f67-104">Por exemplo, uma empresa que tem sua própria implementação de um algoritmo de criptografia pode tornar essa implementação padrão em vez da implementação fornecida no [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="61f67-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span></span> <span data-ttu-id="61f67-105">Embora os aplicativos gerenciados que usam criptografia sempre podem optar por associar explicitamente a uma implementação específica, é recomendável que criar objetos criptográficos usando o sistema de configuração de criptografia.</span><span class="sxs-lookup"><span data-stu-id="61f67-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="61f67-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="61f67-106">In This Section</span></span>  
 [<span data-ttu-id="61f67-107">Mapeando nomes de algoritmo para classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="61f67-107">Mapping Algorithm Names to Cryptography Classes</span></span>](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="61f67-108">Descreve como mapear um nome de algoritmo para uma classe de criptografia.</span><span class="sxs-lookup"><span data-stu-id="61f67-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="61f67-109">Mapeando identificadores de objeto para algoritmos de criptografia</span><span class="sxs-lookup"><span data-stu-id="61f67-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="61f67-110">Descreve como mapear um identificador de objeto para um algoritmo de criptografia.</span><span class="sxs-lookup"><span data-stu-id="61f67-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="61f67-111">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="61f67-111">Related Sections</span></span>  
 [<span data-ttu-id="61f67-112">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="61f67-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 <span data-ttu-id="61f67-113">Fornece uma visão geral dos serviços de criptografia fornecidos pelo [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="61f67-113">Provides an overview of cryptographic services provided by the [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span></span>  
  
 [<span data-ttu-id="61f67-114">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="61f67-114">Cryptography Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 <span data-ttu-id="61f67-115">Descreve os elementos que mapeiam nomes amigáveis de algoritmo a classes que implementam algoritmos de criptografia.</span><span class="sxs-lookup"><span data-stu-id="61f67-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>
