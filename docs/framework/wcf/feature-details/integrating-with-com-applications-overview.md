---
title: Integração com visão geral de aplicativos COM
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: 99e3c2f4445673f3b74048a2b466203af7bc2795
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045891"
---
# <a name="integrating-with-com-applications-overview"></a><span data-ttu-id="63324-102">Integração com visão geral de aplicativos COM</span><span class="sxs-lookup"><span data-stu-id="63324-102">Integrating with COM Applications Overview</span></span>

<span data-ttu-id="63324-103">O Windows Communication Foundation (WCF) fornece ao desenvolvedor de código gerenciado um ambiente avançado para a criação de aplicativos conectados.</span><span class="sxs-lookup"><span data-stu-id="63324-103">Windows Communication Foundation (WCF) provides the managed code developer with a rich environment for creating connected applications.</span></span> <span data-ttu-id="63324-104">No entanto, se você tiver um investimento substancial em código não gerenciado com base em COM e não quiser migrar, você ainda poderá integrar os serviços Web WCF diretamente em seu código existente usando o moniker do serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="63324-104">However, if you have a substantial investment in unmanaged COM-based code and do not want to migrate, you can still integrate WCF Web services directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="63324-105">O moniker do serviço pode ser usado em uma ampla variedade de ambientes de desenvolvimento baseados em COM, como o Office VBA, Visual Basic 6,0 ou C++ Visual 6,0.</span><span class="sxs-lookup"><span data-stu-id="63324-105">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>

> [!NOTE]
> <span data-ttu-id="63324-106">O moniker do serviço usa um canal de comunicação do WCF para toda a comunicação.</span><span class="sxs-lookup"><span data-stu-id="63324-106">The service moniker uses a WCF communication channel for all communication.</span></span> <span data-ttu-id="63324-107">Os mecanismos de segurança e identidade para esse canal diferem daqueles usados em proxies padrão COM e DCOM.</span><span class="sxs-lookup"><span data-stu-id="63324-107">The security and identity mechanisms for that channel differ from those used in standard COM and DCOM proxies.</span></span> <span data-ttu-id="63324-108">Além disso, como o moniker do serviço usa um canal de comunicação do WCF, o período de tempo limite padrão é de um minuto para todas as chamadas.</span><span class="sxs-lookup"><span data-stu-id="63324-108">In addition, because the service moniker uses a WCF communication channel the default timeout period is one minute for all calls.</span></span>

<span data-ttu-id="63324-109">O moniker do serviço é usado com `GetObject` a função para fornecer ao desenvolvedor não gerenciado uma abordagem com rigidez de tipos e específico para chamar serviços Web WCF.</span><span class="sxs-lookup"><span data-stu-id="63324-109">The service moniker is used with the `GetObject` function to provide the unmanaged developer with a strongly-typed, COM-specific approach for calling WCF Web services.</span></span> <span data-ttu-id="63324-110">Isso requer uma definição local e visível do contrato do serviço Web WCF e a associação a ser usada.</span><span class="sxs-lookup"><span data-stu-id="63324-110">This requires a local, COM-visible definition of the WCF Web service contract and the binding that is to be used.</span></span> <span data-ttu-id="63324-111">Assim como outros clientes WCF, o moniker do serviço deve construir um canal digitado para o serviço, embora essa construção de canal ocorra de forma transparente para o programador COM na primeira chamada de método.</span><span class="sxs-lookup"><span data-stu-id="63324-111">Like other WCF clients, the service moniker must construct a typed channel to the service, though this channel construction occurs transparently to the COM programmer on the first method call.</span></span>

<span data-ttu-id="63324-112">Em comum com outros clientes WCF, ao usar o moniker, os aplicativos especificam o endereço, a associação e o contrato para se comunicar com um serviço.</span><span class="sxs-lookup"><span data-stu-id="63324-112">In common with other WCF clients, when using the moniker, applications specify the address, binding and contract to communicate with a service.</span></span> <span data-ttu-id="63324-113">O contrato pode ser especificado de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="63324-113">The contract can be specified in one of the following ways:</span></span>

- <span data-ttu-id="63324-114">Contrato tipado – o contrato é registrado como um tipo visível COM no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="63324-114">Typed contract – the contract is registered as a COM visible type on the client machine.</span></span>

- <span data-ttu-id="63324-115">Contrato WSDL – o contrato é fornecido na forma de um documento WSDL.</span><span class="sxs-lookup"><span data-stu-id="63324-115">WSDL contract – the contract is supplied in the form of a WSDL document.</span></span>

- <span data-ttu-id="63324-116">Contrato MEX – o contrato é recuperado em tempo de execução de um ponto de extremidade de intercâmbio de metadados (MEX).</span><span class="sxs-lookup"><span data-stu-id="63324-116">MEX contract – the contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>

## <a name="parameters-supported-by-the-service-moniker"></a><span data-ttu-id="63324-117">Parâmetros com suporte no moniker do serviço</span><span class="sxs-lookup"><span data-stu-id="63324-117">Parameters Supported by the Service Moniker</span></span>

<span data-ttu-id="63324-118">A tabela a seguir mostra os parâmetros que são suportados pelo moniker do serviço.</span><span class="sxs-lookup"><span data-stu-id="63324-118">The following table shows the parameters that are supported by the service moniker.</span></span>

|<span data-ttu-id="63324-119">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="63324-119">Parameter</span></span>|<span data-ttu-id="63324-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="63324-120">Description</span></span>|
|---------------|-----------------|
|`address`|<span data-ttu-id="63324-121">Local da URL do serviço.</span><span class="sxs-lookup"><span data-stu-id="63324-121">URL location of the service.</span></span>|
|`binding`|<span data-ttu-id="63324-122">Nome da seção de associação da configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="63324-122">Binding section name from the application configuration.</span></span>|
|`bindingConfiguration`|<span data-ttu-id="63324-123">Instância de associação nomeada de dentro da seção de associação nomeada.</span><span class="sxs-lookup"><span data-stu-id="63324-123">Named binding instance from within the named binding section.</span></span>|
|`contract`|<span data-ttu-id="63324-124">Identificador de interface (IID) que representa o contrato de serviço ou o nome do contrato (de MEX).</span><span class="sxs-lookup"><span data-stu-id="63324-124">Interface identifier (IID) that represents the service contract or the contract name (from MEX).</span></span>|
|`wsdl`|<span data-ttu-id="63324-125">Documento WSDL que fornece uma forma alternativa de definição de contrato.</span><span class="sxs-lookup"><span data-stu-id="63324-125">WSDL document that provides an alternative form of contract definition.</span></span>|
|`spnIdentity`|<span data-ttu-id="63324-126">A identidade do SPN (nome principal do servidor) a ser usada para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="63324-126">Server principal name (SPN) identity to be used to communicate with the service.</span></span>|
|`upnIdentity`|<span data-ttu-id="63324-127">Identidade de UPN (nome principal do usuário) a ser usada para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="63324-127">User principal name (UPN) identity to be used to communicate with the service.</span></span>|
|`dnsIdentity`|<span data-ttu-id="63324-128">Identidade DNS a ser usada para se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="63324-128">DNS identity to be used to communicate with the service.</span></span>|
|`mexAddress`|<span data-ttu-id="63324-129">Local da URL do ponto de extremidade de intercâmbio de metadados (MEX) do serviço.</span><span class="sxs-lookup"><span data-stu-id="63324-129">URL location of the Metadata Exchange (MEX) endpoint of the service.</span></span>|
|`mexBinding`|<span data-ttu-id="63324-130">Nome da seção de associação da configuração do aplicativo para se conectar ao ponto de extremidade MEX.</span><span class="sxs-lookup"><span data-stu-id="63324-130">Binding section name from the application configuration to connect with the MEX endpoint.</span></span>|
|`mexBindingConfiguration`|<span data-ttu-id="63324-131">Instância de associação nomeada de dentro da seção de associação nomeada para se conectar ao ponto de extremidade MEX.</span><span class="sxs-lookup"><span data-stu-id="63324-131">Named binding instance from within the named binding section to connect with the MEX endpoint.</span></span>|
|`bindingNamespace`|<span data-ttu-id="63324-132">Namespace do nome da seção de associação do MEX recuperado.</span><span class="sxs-lookup"><span data-stu-id="63324-132">Namespace of the binding section name from the retrieved MEX.</span></span>|
|`contractNamespace`|<span data-ttu-id="63324-133">Namespace do contrato do MEX recuperado.</span><span class="sxs-lookup"><span data-stu-id="63324-133">Namespace of the contract from the retrieved MEX.</span></span>|
|`mexSpnIdentity`|<span data-ttu-id="63324-134">A identidade do SPN (nome principal do servidor) a ser usada para se comunicar com o ponto de extremidade MEX.</span><span class="sxs-lookup"><span data-stu-id="63324-134">Server principal name (SPN) identity to be used to communicate with the MEX endpoint.</span></span>|
|`mexUpnIdentity`|<span data-ttu-id="63324-135">Identidade de UPN (nome principal do usuário) a ser usada para se comunicar com o ponto de extremidade MEX.</span><span class="sxs-lookup"><span data-stu-id="63324-135">User principal name (UPN) identity to be used to communicate with the MEX endpoint.</span></span>|
|`mexDnsIdentity`|<span data-ttu-id="63324-136">Identidade DNS a ser usada para se comunicar com o ponto de extremidade MEX.</span><span class="sxs-lookup"><span data-stu-id="63324-136">DNS identity to be used to communicate with the MEX endpoint.</span></span>|
|`serializer`|<span data-ttu-id="63324-137">Especifique o uso do serializador "XML" ou "DataContract".</span><span class="sxs-lookup"><span data-stu-id="63324-137">Specify the use of either the "xml" or "datacontract" serializer.</span></span>|

> [!NOTE]
> <span data-ttu-id="63324-138">Mesmo quando usado com clientes totalmente baseados em COM, o moniker do serviço exige que o WCF e o suporte ao .NET Framework 2,0 sejam instalados no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="63324-138">Even when used with entirely COM-based clients, the service moniker requires WCF and the supporting .NET Framework 2.0 to be installed on the client computer.</span></span> <span data-ttu-id="63324-139">Também é essencial que os aplicativos cliente que usam o moniker do serviço carreguem a versão apropriada do tempo de execução de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="63324-139">It is also critical that client applications that use the service moniker load the appropriate version of the .NET Framework runtime.</span></span> <span data-ttu-id="63324-140">Ao usar o moniker em aplicativos do Office, um arquivo de configuração pode ser necessário para garantir que a versão correta da estrutura seja carregada.</span><span class="sxs-lookup"><span data-stu-id="63324-140">When using the moniker within Office applications, a configuration file may be required to ensure that the correct framework version is loaded.</span></span> <span data-ttu-id="63324-141">Por exemplo, com o Excel, o texto a seguir deve ser colocado em um arquivo chamado Excel. exe. config no mesmo diretório que o arquivo Excel. exe:</span><span class="sxs-lookup"><span data-stu-id="63324-141">For example, with Excel, the following text should be placed in a file called Excel.exe.config in the same directory as the Excel.exe file:</span></span>
>
> `<?xml version="1.0" encoding="utf-8"?>`
>
> <span data-ttu-id="63324-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span><span class="sxs-lookup"><span data-stu-id="63324-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span></span>
>
> `<startup>`
>
> `<requiredRuntime version="v2.0.50727" />`
>
> `</startup>`
>
> `</configuration>`

## <a name="see-also"></a><span data-ttu-id="63324-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63324-143">See also</span></span>

- [<span data-ttu-id="63324-144">Como: Registrar e configurar um moniker de serviço</span><span class="sxs-lookup"><span data-stu-id="63324-144">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
