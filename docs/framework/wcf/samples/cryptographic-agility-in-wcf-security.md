---
title: Agilidade de criptografia na segurança do WCF
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: 2dbacd53876ded76ea212dd5656cd2dded4a6e48
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714933"
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="a5732-102">Agilidade de criptografia na segurança do WCF</span><span class="sxs-lookup"><span data-stu-id="a5732-102">Cryptographic agility in WCF security</span></span>

<span data-ttu-id="a5732-103">Este exemplo mostra como especificar em um algoritmo padrão/personalizado para fornecer uma implementação ágil de criptografia em um cliente e serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a5732-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a Windows Communication Foundation (WCF) client and service.</span></span> <span data-ttu-id="a5732-104">O exemplo é composto pelos seguintes projetos:</span><span class="sxs-lookup"><span data-stu-id="a5732-104">The sample is composed of the following projects:</span></span>

<span data-ttu-id="a5732-105">**Serviço**</span><span class="sxs-lookup"><span data-stu-id="a5732-105">**Service**</span></span>

<span data-ttu-id="a5732-106">Este é um serviço WCF auto-hospedado que implementa a interface `ICalculator` e protege o ponto de extremidade usando o <xref:System.ServiceModel.WSHttpBinding> com sessão segura e sessão confiável desabilitada.</span><span class="sxs-lookup"><span data-stu-id="a5732-106">This is a self-hosted WCF service that implements the `ICalculator` interface and secures the endpoint using the <xref:System.ServiceModel.WSHttpBinding> with secure session and reliable session disabled.</span></span> <span data-ttu-id="a5732-107">O serviço define uma classe de `SecurityAlgorithmSuite` personalizada para especificar os algoritmos criptográficos a serem usados para segurança de mensagens.</span><span class="sxs-lookup"><span data-stu-id="a5732-107">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

<span data-ttu-id="a5732-108">**Cliente**</span><span class="sxs-lookup"><span data-stu-id="a5732-108">**Client**</span></span>

<span data-ttu-id="a5732-109">Esse é um cliente WCF que acessa o serviço após a autenticação bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="a5732-109">This is a WCF client that accesses the service after successful authentication.</span></span> <span data-ttu-id="a5732-110">Ele invoca as operações expostas pela interface `ICalculator` e implementada pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="a5732-110">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="a5732-111">O cliente também define a mesma classe de `SecurityAlgorithmSuite` personalizada para especificar os algoritmos criptográficos a serem usados para segurança de mensagens.</span><span class="sxs-lookup"><span data-stu-id="a5732-111">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

## <a name="to-use-this-sample"></a><span data-ttu-id="a5732-112">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="a5732-112">To use this sample</span></span>

1. <span data-ttu-id="a5732-113">Abra a solução CryptoAgility. sln no Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="a5732-113">Open the CryptoAgility.sln solution in Visual Studio 2012.</span></span>

2. <span data-ttu-id="a5732-114">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="a5732-114">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="a5732-115">Abra o explorador de arquivos e navegue até o diretório \WCF\Basic\Security\CryptoAgility\Service\bin e execute o arquivo Service. exe com privilégios de administrador clicando com o botão direito do mouse em Service. exe e selecionando **Executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="a5732-115">Open File Explorer and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>

4. <span data-ttu-id="a5732-116">Navegue até o diretório \WCF\Basic\Security\CryptoAgility\Client\bin e execute o arquivo client. exe normalmente.</span><span class="sxs-lookup"><span data-stu-id="a5732-116">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a5732-117">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="a5732-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a5732-118">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="a5732-118">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="a5732-119">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="a5732-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a5732-120">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="a5732-120">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a><span data-ttu-id="a5732-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5732-121">See also</span></span>

- [<span data-ttu-id="a5732-122">Segurança de Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="a5732-122">Windows Communication Foundation Security</span></span>](../feature-details/security.md)
