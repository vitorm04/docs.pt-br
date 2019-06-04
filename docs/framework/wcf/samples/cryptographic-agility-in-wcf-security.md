---
title: Agilidade criptográfica de segurança do WCF
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: b8e3b6dc62baf31901520d7f5edac0529e937016
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490943"
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="d31f7-102">Agilidade criptográfica de segurança do WCF</span><span class="sxs-lookup"><span data-stu-id="d31f7-102">Cryptographic agility in WCF security</span></span>

<span data-ttu-id="d31f7-103">Este exemplo mostra como especificar em um algoritmo padrão/personalizadas para fornecer uma implementação criptográfica agile em um cliente do Windows Communication Foundation (WCF) e o serviço.</span><span class="sxs-lookup"><span data-stu-id="d31f7-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a Windows Communication Foundation (WCF) client and service.</span></span> <span data-ttu-id="d31f7-104">O exemplo é composto de projetos a seguir:</span><span class="sxs-lookup"><span data-stu-id="d31f7-104">The sample is composed of the following projects:</span></span>

<span data-ttu-id="d31f7-105">**Serviço**</span><span class="sxs-lookup"><span data-stu-id="d31f7-105">**Service**</span></span>

<span data-ttu-id="d31f7-106">Isso é um serviço WCF auto-hospedado que implementa o `ICalculator` da interface e protege o ponto de extremidade usando o <xref:System.ServiceModel.WSHttpBinding> com sessão segura e confiável sessão desabilitada.</span><span class="sxs-lookup"><span data-stu-id="d31f7-106">This is a self-hosted WCF service that implements the `ICalculator` interface and secures the endpoint using the <xref:System.ServiceModel.WSHttpBinding> with secure session and reliable session disabled.</span></span> <span data-ttu-id="d31f7-107">O serviço define um personalizado `SecurityAlgorithmSuite` classe para especificar os algoritmos de criptografia a ser usado para segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="d31f7-107">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

<span data-ttu-id="d31f7-108">**Cliente**</span><span class="sxs-lookup"><span data-stu-id="d31f7-108">**Client**</span></span>

<span data-ttu-id="d31f7-109">Isso é um cliente do WCF que acessa o serviço após uma autenticação bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d31f7-109">This is a WCF client that accesses the service after successful authentication.</span></span> <span data-ttu-id="d31f7-110">Ele invoca as operações expostas pelo `ICalculator` de interface e implementadas pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="d31f7-110">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="d31f7-111">O cliente também define a mesma personalizada `SecurityAlgorithmSuite` classe para especificar os algoritmos de criptografia a ser usado para segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="d31f7-111">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

## <a name="to-use-this-sample"></a><span data-ttu-id="d31f7-112">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="d31f7-112">To use this sample</span></span>

1. <span data-ttu-id="d31f7-113">Abra a solução de CryptoAgility.sln no Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="d31f7-113">Open the CryptoAgility.sln solution in Visual Studio 2012.</span></span>

2. <span data-ttu-id="d31f7-114">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="d31f7-114">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="d31f7-115">Abra o Explorador de arquivos, navegue até o diretório \WCF\Basic\Security\CryptoAgility\Service\bin e execute o arquivo de service.exe com privilégios de administrador service.exe botão direito do mouse e selecionando **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="d31f7-115">Open File Explorer and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>

4. <span data-ttu-id="d31f7-116">Navegue até o diretório \WCF\Basic\Security\CryptoAgility\Client\bin e execute o arquivo client.exe normalmente.</span><span class="sxs-lookup"><span data-stu-id="d31f7-116">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d31f7-117">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="d31f7-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d31f7-118">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="d31f7-118">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="d31f7-119">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="d31f7-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d31f7-120">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="d31f7-120">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a><span data-ttu-id="d31f7-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d31f7-121">See also</span></span>

- [<span data-ttu-id="d31f7-122">Segurança do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d31f7-122">Windows Communication Foundation Security</span></span>](../feature-details/security.md)
