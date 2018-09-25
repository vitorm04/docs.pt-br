---
title: Misturando protocolos confiáveis em cenários federados
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
author: BrucePerlerMS
ms.openlocfilehash: d4290880d8d708811a95b38356aa61f0d23c89a8
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47090364"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a><span data-ttu-id="3db15-102">Misturando protocolos confiáveis em cenários federados</span><span class="sxs-lookup"><span data-stu-id="3db15-102">Mixing Trust Protocols in Federated Scenarios</span></span>
<span data-ttu-id="3db15-103">Pode haver situações em que os clientes federados se comunicar com um serviço e um serviço de Token de segurança (STS) que não têm a mesma versão de confiança.</span><span class="sxs-lookup"><span data-stu-id="3db15-103">There may be scenarios in which federated clients communicate with a service and a Security Token Service (STS) that do not have the same trust version.</span></span> <span data-ttu-id="3db15-104">O serviço WSDL pode conter um `RequestSecurityTokenTemplate` asserção com elementos de WS-Trust que são de versões diferentes do que o STS.</span><span class="sxs-lookup"><span data-stu-id="3db15-104">The service WSDL can contain a `RequestSecurityTokenTemplate` assertion with WS-Trust elements that are of different versions than the STS.</span></span> <span data-ttu-id="3db15-105">Nesses casos, um cliente do Windows Communication Foundation (WCF) converte os elementos de WS-Trust proveniente do `RequestSecurityTokenTemplate` para coincidir com o STS confiar versão.</span><span class="sxs-lookup"><span data-stu-id="3db15-105">In such cases, a Windows Communication Foundation (WCF) client converts the WS-Trust elements received from the `RequestSecurityTokenTemplate` to match the STS trust version.</span></span> <span data-ttu-id="3db15-106">WCF trata versões incompatíveis confiança apenas para associações padrão.</span><span class="sxs-lookup"><span data-stu-id="3db15-106">WCF handles mismatched trust versions only for standard bindings.</span></span> <span data-ttu-id="3db15-107">Todos os parâmetros de algoritmo padrão que são reconhecidos por WCF fazem parte da associação padrão.</span><span class="sxs-lookup"><span data-stu-id="3db15-107">All standard algorithm parameters that are recognized by WCF are part of the standard binding.</span></span> <span data-ttu-id="3db15-108">Este tópico descreve o comportamento do WCF com várias configurações de confiança entre o serviço e o STS.</span><span class="sxs-lookup"><span data-stu-id="3db15-108">This topic describes the WCF behavior with various trust settings between the service and the STS.</span></span>  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a><span data-ttu-id="3db15-109">RP de fevereiro de 2005 e fevereiro de 2005 do STS</span><span class="sxs-lookup"><span data-stu-id="3db15-109">RP Feb 2005 and STS Feb 2005</span></span>  
 <span data-ttu-id="3db15-110">O WSDL para terceiros da terceira parte confiável (RP) contém os seguintes elementos dentro de `RequestSecurityTokenTemplate` seção:</span><span class="sxs-lookup"><span data-stu-id="3db15-110">The WSDL for Relying Party (RP) contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="3db15-111">O arquivo de configuração do cliente contém uma lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="3db15-111">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="3db15-112">O WCF não consegue diferenciar entre os parâmetros de cliente e o serviço; Adiciona todos os parâmetros e as envia no `RequestSecurityTokenTemplate` (RST).</span><span class="sxs-lookup"><span data-stu-id="3db15-112">WCF cannot differentiate between the client and service parameters; it adds all the parameters and sends them in the `RequestSecurityTokenTemplate` (RST).</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-13"></a><span data-ttu-id="3db15-113">Relação de confiança RP 1.3 e STS Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="3db15-113">RP Trust 1.3 and STS Trust 1.3</span></span>  
 <span data-ttu-id="3db15-114">O WSDL para RP contém os seguintes elementos dentro de `RequestSecurityTokenTemplate` seção:</span><span class="sxs-lookup"><span data-stu-id="3db15-114">The WSDL for RP contains the following elements within the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="3db15-115">O arquivo de configuração de cliente contém um `secondaryParameters` elemento que encapsula os parâmetros especificados pela RP.</span><span class="sxs-lookup"><span data-stu-id="3db15-115">The client configuration file contains a `secondaryParameters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="3db15-116">O WCF remove o `EncryptionAlgorithm`, `CanonicalizationAlgorithm` e `KeyWrapAlgorithm` elementos do elemento de nível superior sob o RST se elas estiverem presentes dentro a `SecondaryParameters` elemento.</span><span class="sxs-lookup"><span data-stu-id="3db15-116">WCF removes the `EncryptionAlgorithm`, `CanonicalizationAlgorithm` and `KeyWrapAlgorithm` elements from the top-level element under the RST if these are present inside the `SecondaryParameters` element.</span></span> <span data-ttu-id="3db15-117">O WCF anexa o `SecondaryParameters` elemento RST de saída sem modificações.</span><span class="sxs-lookup"><span data-stu-id="3db15-117">WCF appends the `SecondaryParameters` element to the outgoing RST unmodified.</span></span>  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a><span data-ttu-id="3db15-118">Relação de confiança RP fevereiro de 2005 e o STS Trust 1.3</span><span class="sxs-lookup"><span data-stu-id="3db15-118">RP Trust Feb 2005 and STS Trust 1.3</span></span>  
 <span data-ttu-id="3db15-119">O WSDL para RP contém os seguintes elementos de `RequestSecurityTokenTemplate` seção:</span><span class="sxs-lookup"><span data-stu-id="3db15-119">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
 <span data-ttu-id="3db15-120">O arquivo de configuração do cliente contém uma lista de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="3db15-120">The client configuration file contains a list of parameters.</span></span>  
  
 <span data-ttu-id="3db15-121">Do arquivo de configuração de cliente, o WCF não consegue diferenciar entre os parâmetros de serviço e cliente.</span><span class="sxs-lookup"><span data-stu-id="3db15-121">From the client configuration file, WCF cannot differentiate between the service and client parameters.</span></span> <span data-ttu-id="3db15-122">Portanto, o WCF converte todos os parâmetros em um namespace de versão 1.3 da relação de confiança.</span><span class="sxs-lookup"><span data-stu-id="3db15-122">Therefore WCF converts all the parameters to a Trust version 1.3 namespace.</span></span>  
  
 <span data-ttu-id="3db15-123">Alças do WCF a `KeyType`, `KeySize`, e `TokenType` elementos da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="3db15-123">WCF handles the `KeyType`, `KeySize`, and `TokenType` elements as follows:</span></span>  
  
-   <span data-ttu-id="3db15-124">Baixar WSDL, criar uma associação e atribua `KeyType`, `KeySize`, e `TokenType` dos parâmetros de RP.</span><span class="sxs-lookup"><span data-stu-id="3db15-124">Download the WSDL, create the binding, and assign `KeyType`, `KeySize`, and `TokenType` from the RP parameters.</span></span> <span data-ttu-id="3db15-125">O arquivo de configuração do cliente é gerado.</span><span class="sxs-lookup"><span data-stu-id="3db15-125">The client configuration file is then generated.</span></span>  
  
-   <span data-ttu-id="3db15-126">O cliente agora pode alterar qualquer parâmetro no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="3db15-126">The client can now change any parameter in the configuration file.</span></span>  
  
-   <span data-ttu-id="3db15-127">Durante o tempo de execução, o WCF copia todos os parâmetros especificados para o `AdditionalTokenParameters` seção do arquivo de configuração do cliente, exceto `KeyType`, `KeySize` e `TokenType`, porque esses parâmetros sejam levados em conta durante o arquivo de configuração geração.</span><span class="sxs-lookup"><span data-stu-id="3db15-127">During runtime, WCF copies all parameters specified into the `AdditionalTokenParameters` section of the client configuration file except `KeyType`, `KeySize` and `TokenType`, because these parameters are accounted for during the configuration file generation.</span></span>  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a><span data-ttu-id="3db15-128">Relação de confiança RP 1.3 e STS Trust fevereiro de 2005</span><span class="sxs-lookup"><span data-stu-id="3db15-128">RP Trust 1.3 and STS Trust Feb 2005</span></span>  
 <span data-ttu-id="3db15-129">O WSDL para RP contém os seguintes elementos de `RequestSecurityTokenTemplate` seção:</span><span class="sxs-lookup"><span data-stu-id="3db15-129">The WSDL for RP contains the following elements in the `RequestSecurityTokenTemplate` section:</span></span>  
  
-   `CanonicalizationAlgorithm`  
  
-   `EncryptionAlgorithm`  
  
-   `EncryptWith`  
  
-   `SignWith`  
  
-   `KeySize`  
  
-   `KeyType`  
  
-   `KeyWrapAlgorithm`  
  
 <span data-ttu-id="3db15-130">O arquivo de configuração de cliente contém um `secondaryParamters` elemento que encapsula os parâmetros especificados pela RP.</span><span class="sxs-lookup"><span data-stu-id="3db15-130">The client configuration file contains a `secondaryParamters` element that wraps the parameters specified by the RP.</span></span>  
  
 <span data-ttu-id="3db15-131">WCF copia todos os parâmetros especificados dentro de `SecondaryParameters` seção ao elemento RST de nível superior, mas não convertê-los para o namespace do WS-Trust de 2005.</span><span class="sxs-lookup"><span data-stu-id="3db15-131">WCF copies all the parameters specified within the `SecondaryParameters` section to the top-level RST element, but does not convert them to the 2005 WS-Trust namespace.</span></span>
