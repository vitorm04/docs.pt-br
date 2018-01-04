---
title: "Agilidade criptográfica de segurança do WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7d99ada67255d0ced8bbabc2ab6fc645e6ba9e35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="11b58-102">Agilidade criptográfica de segurança do WCF</span><span class="sxs-lookup"><span data-stu-id="11b58-102">Cryptographic Agility in WCF Security</span></span>
<span data-ttu-id="11b58-103">Este exemplo mostra como especificar um algoritmo de standard/personalizada para fornecer uma implementação criptográfica agile em um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] cliente e serviço.</span><span class="sxs-lookup"><span data-stu-id="11b58-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service.</span></span> <span data-ttu-id="11b58-104">O exemplo é composto dos seguintes projetos:</span><span class="sxs-lookup"><span data-stu-id="11b58-104">The sample is composed of the following projects:</span></span>  
  
 <span data-ttu-id="11b58-105">Serviço</span><span class="sxs-lookup"><span data-stu-id="11b58-105">Service</span></span>  
 <span data-ttu-id="11b58-106">Este é um auto-hospedado [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço que implementa o `ICalculator` interface e protege o ponto de extremidade usando o <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> com a sessão segura e confiável de sessão desabilitada.</span><span class="sxs-lookup"><span data-stu-id="11b58-106">This is a self-hosted [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that implements the `ICalculator` interface and secures the endpoint using the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> with secure session and reliable session disabled.</span></span> <span data-ttu-id="11b58-107">O serviço define um personalizado `SecurityAlgorithmSuite` classe para especificar os algoritmos de criptografia a ser usado para segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="11b58-107">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
 <span data-ttu-id="11b58-108">Cliente</span><span class="sxs-lookup"><span data-stu-id="11b58-108">Client</span></span>  
 <span data-ttu-id="11b58-109">Este é um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]cliente que acessa o serviço após a autenticação bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="11b58-109">This is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]client that accesses the service after successful authentication.</span></span> <span data-ttu-id="11b58-110">Invocar operações expostas pelo `ICalculator` interface e implementados pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="11b58-110">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="11b58-111">O cliente também define o mesmo personalizado `SecurityAlgorithmSuite` classe para especificar os algoritmos de criptografia a ser usado para segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="11b58-111">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="11b58-112">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="11b58-112">To use this sample</span></span>  
  
1.  <span data-ttu-id="11b58-113">Abra a solução CryptoAgility.sln em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11b58-113">Open the CryptoAgility.sln solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="11b58-114">Pressione CTRL+SHIFT+B para criar a solução.</span><span class="sxs-lookup"><span data-stu-id="11b58-114">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="11b58-115">Abra [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] e navegue até o diretório \WCF\Basic\Security\CryptoAgility\Service\bin e execute o arquivo de service.exe com privilégios de administrador, clicando duas vezes service.exe e selecionando **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="11b58-115">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>  
  
4.  <span data-ttu-id="11b58-116">Navegue até o diretório \WCF\Basic\Security\CryptoAgility\Client\bin e execute o arquivo client.exe normalmente.</span><span class="sxs-lookup"><span data-stu-id="11b58-116">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="11b58-117">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="11b58-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="11b58-118">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="11b58-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="11b58-119">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="11b58-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="11b58-120">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="11b58-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a><span data-ttu-id="11b58-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="11b58-121">See Also</span></span>  
 [<span data-ttu-id="11b58-122">Segurança</span><span class="sxs-lookup"><span data-stu-id="11b58-122">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
