---
title: "Misturando protocolos confiáveis em cenários federados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7031e222b152bfa61e13e0e4a44b5ad9418b07c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="2046c-102">Misturando protocolos confiáveis em cenários federados</span><span class="sxs-lookup"><span data-stu-id="2046c-102">Mixing Trust Protocols in Federated Scenarios</span></span>
<span data-ttu-id="2046c-103">Pode haver cenários em que os clientes federados se comunicar com um serviço e um serviço de Token de segurança (STS) que não têm a mesma versão de confiança.</span><span class="sxs-lookup"><span data-stu-id="2046c-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="2046c-104">O serviço WSDL pode conter um `RequestSecurityTokenTemplate` asserção com elementos de WS-Trust das versões diferentes do que o STS.</span><span class="sxs-lookup"><span data-stu-id="2046c-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="2046c-105">Nesses casos, um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] cliente converte os elementos de WS-Trust recebidos do `RequestSecurityTokenTemplate` para corresponder o STS confiança versão.</span><span class="sxs-lookup"><span data-stu-id="2046c-105">In such cases, a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2046c-106">versões de relação de confiança de identificadores incompatíveis somente para associações padrão.</span><span class="sxs-lookup"><span data-stu-id="2046c-106"> handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="2046c-107">Todos os parâmetros de algoritmo padrão que são reconhecidos pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fazem parte da associação padrão.</span><span class="sxs-lookup"><span data-stu-id="2046c-107">All standard algorithm parameters that are recognized by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] are part of the standard binding.</span></span> <span data-ttu-id="2046c-108">Este tópico descreve o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] comportamento com várias configurações entre o serviço e o STS de relação de confiança.</span><span class="sxs-lookup"><span data-stu-id="2046c-108">This topic describes the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="2046c-109">RP fevereiro de 2005 e STS fevereiro de 2005</span><span class="sxs-lookup"><span data-stu-id="2046c-109">RP Feb 2005 and STS Feb 2005</span></span>  
 <span data-ttu-id="2046c-110">O WSDL para terceira parte confiável (RP) contém os seguintes elementos dentro de `RequestSecurityTokenTemplate` seção:</span><span class="sxs-lookup"><span data-stu-id="2046c-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="2046c-111">O arquivo de configuração do cliente contém uma lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="2046c-111">The client configuration file contains a list of parameters.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2046c-112">não é possível diferenciar entre os parâmetros de cliente e de serviço; Adiciona todos os parâmetros e as envia no `RequestSecurityTokenTemplate` (primeira).</span><span class="sxs-lookup"><span data-stu-id="2046c-112"> cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="2046c-113">RP Trust 1.3 e STS Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="2046c-113">RP Trust 1.3 and STS Trust 1.3</span></span>  
 <span data-ttu-id="2046c-114">O WSDL para RP contém os seguintes elementos dentro de `RequestSecurityTokenTemplate` seção:</span><span class="sxs-lookup"><span data-stu-id="2046c-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="2046c-115">O arquivo de configuração do cliente contém um `secondaryParameters` elemento que encapsula os parâmetros especificados pela RP.</span><span class="sxs-lookup"><span data-stu-id="2046c-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2046c-116">Remove o `EncryptionAlgorithm`, `CanonicalizationAlgorithm` e `KeyWrapAlgorithm` elementos do elemento de nível superior na primeira se estes estiverem dentro do `SecondaryParameters` elemento.</span><span class="sxs-lookup"><span data-stu-id="2046c-116"> removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2046c-117">acrescenta o `SecondaryParameters` elemento para a primeira saída sem modificações.</span><span class="sxs-lookup"><span data-stu-id="2046c-117"> appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="2046c-118">Relação de confiança do RP fevereiro de 2005 e STS Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="2046c-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  
 <span data-ttu-id="2046c-119">O WSDL para RP contém os seguintes elementos de `RequestSecurityTokenTemplate` seção:</span><span class="sxs-lookup"><span data-stu-id="2046c-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="2046c-120">O arquivo de configuração do cliente contém uma lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="2046c-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="2046c-121">No arquivo de configuração de cliente, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não é possível diferenciar entre os parâmetros de cliente e de serviço.</span><span class="sxs-lookup"><span data-stu-id="2046c-121">From the client configuration file, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="2046c-122">Portanto, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] converte todos os parâmetros em um namespace de versão 1.3 de confiança.</span><span class="sxs-lookup"><span data-stu-id="2046c-122">Therefore [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2046c-123">identificadores de `KeyType`, `KeySize`, e `TokenType` elementos da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="2046c-123"> handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
-   <span data-ttu-id="2046c-124">Baixar WSDL, criar a associação e atribuir `KeyType`, `KeySize`, e `TokenType` de parâmetros de RP.</span><span class="sxs-lookup"><span data-stu-id="2046c-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="2046c-125">O arquivo de configuração do cliente é gerado.</span><span class="sxs-lookup"><span data-stu-id="2046c-125">The client configuration file is then generated.</span></span>  
  
-   <span data-ttu-id="2046c-126">O cliente agora pode alterar qualquer parâmetro no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="2046c-126">The client can now change any parameter in the configuration file.</span></span>  
  
-   <span data-ttu-id="2046c-127">Durante a execução, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] copia todos os parâmetros especificados para o `AdditionalTokenParameters` seção do arquivo de configuração do cliente, exceto `KeyType`, `KeySize` e `TokenType`, porque esses parâmetros são tratados de durante a configuração geração de arquivo.</span><span class="sxs-lookup"><span data-stu-id="2046c-127">During runtime, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="2046c-128">RP Trust 1.3 e a confiança do STS fevereiro de 2005</span><span class="sxs-lookup"><span data-stu-id="2046c-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  
 <span data-ttu-id="2046c-129">O WSDL para RP contém os seguintes elementos de `RequestSecurityTokenTemplate` seção:</span><span class="sxs-lookup"><span data-stu-id="2046c-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="2046c-130">O arquivo de configuração do cliente contém um `secondaryParamters` elemento que encapsula os parâmetros especificados pela RP.</span><span class="sxs-lookup"><span data-stu-id="2046c-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2046c-131">copia todos os parâmetros especificados dentro de `SecondaryParameters` seção para o elemento de nível superior primeira, mas não convertê-los para o namespace de WS-Trust 2005.</span><span class="sxs-lookup"><span data-stu-id="2046c-131"> copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
