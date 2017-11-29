---
title: "Ativação de XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 486760e2-bb10-4ed5-8c02-fe7472498d2d
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f513b10c84de968d5a18b800037b512aad90399e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="xaml-activation"></a><span data-ttu-id="137b3-102">Ativação de XAML</span><span class="sxs-lookup"><span data-stu-id="137b3-102">XAML Activation</span></span>
<span data-ttu-id="137b3-103">Este exemplo demonstra como hospedar um fluxo de trabalho declarativo no IIS.</span><span class="sxs-lookup"><span data-stu-id="137b3-103">This sample demonstrates how to host a declarative workflow in IIS.</span></span> <span data-ttu-id="137b3-104">O exemplo é um fluxo de trabalho básico chamado `EchoService` que tenha uma operação.</span><span class="sxs-lookup"><span data-stu-id="137b3-104">The sample is a basic workflow called `EchoService` that has one operation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="137b3-105">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="137b3-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="137b3-106">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="137b3-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="137b3-107">Se este diretório não existe, vá (página de download) baixar todos os exemplos de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e de [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="137b3-107">If this directory does not exist, go to (download page) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="137b3-108">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="137b3-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLActivation`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="137b3-109">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="137b3-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="137b3-110">Abra a solução de XAMLActivation.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="137b3-110">Open the XAMLActivation.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="137b3-111">Compile a solução pressionando **F5**.</span><span class="sxs-lookup"><span data-stu-id="137b3-111">Build the solution by pressing **F5**.</span></span>  
  
3.  <span data-ttu-id="137b3-112">Execução WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="137b3-112">Run WcfTestClient.exe.</span></span> <span data-ttu-id="137b3-113">Do prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="137b3-113">From a command prompt, type in the following:</span></span>  
  
    1.  <span data-ttu-id="137b3-114">CD %SystemDrive% \ program files \ Microsoft Visual Studio 10.0 \ Common7 \ IDE</span><span class="sxs-lookup"><span data-stu-id="137b3-114">cd %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE</span></span>  
  
    2.  <span data-ttu-id="137b3-115">Execução WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="137b3-115">Run WcfTestClient.exe.</span></span>  
  
4.  <span data-ttu-id="137b3-116">Defina o endereço de serviço em WcfTestClient.exe pressionando CTRL+SHIFT+A e definindo o endereço de serviço a http://localhost:56133/Service.xamlx.</span><span class="sxs-lookup"><span data-stu-id="137b3-116">Set the address of the service on WcfTestClient.exe by pressing CTRL+SHIFT+A and setting the service address to http://localhost:56133/Service.xamlx.</span></span>  
  
5.  <span data-ttu-id="137b3-117">Executar a operação de eco para testar o serviço.</span><span class="sxs-lookup"><span data-stu-id="137b3-117">Perform the echo operation to test the service.</span></span>  
  
6.  <span data-ttu-id="137b3-118">Implantar o serviço no IIS usando DeployToIIS.Bat em um prompt de comando com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="137b3-118">Deploy the Service in IIS using DeployToIIS.Bat in a command prompt with administrator privileges.</span></span>  
  
7.  <span data-ttu-id="137b3-119">Atualizar o endereço do serviço no cliente a http://localhost/XAMLActivation/Service.xamlx e testar o serviço que usa novamente WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="137b3-119">Update the service address in the client to http://localhost/XAMLActivation/Service.xamlx and test the service again using WcfTestClient.exe.</span></span>
