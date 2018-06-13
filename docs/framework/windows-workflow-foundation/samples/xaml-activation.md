---
title: Ativação de XAML
ms.date: 03/30/2017
ms.assetid: 486760e2-bb10-4ed5-8c02-fe7472498d2d
ms.openlocfilehash: 8621b0ea7b390c81e76ac7eeedb0b547b44320d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517706"
---
# <a name="xaml-activation"></a><span data-ttu-id="a6213-102">Ativação de XAML</span><span class="sxs-lookup"><span data-stu-id="a6213-102">XAML Activation</span></span>
<span data-ttu-id="a6213-103">Este exemplo demonstra como hospedar um fluxo de trabalho declarativo no IIS.</span><span class="sxs-lookup"><span data-stu-id="a6213-103">This sample demonstrates how to host a declarative workflow in IIS.</span></span> <span data-ttu-id="a6213-104">O exemplo é um fluxo de trabalho básico chamado `EchoService` que tenha uma operação.</span><span class="sxs-lookup"><span data-stu-id="a6213-104">The sample is a basic workflow called `EchoService` that has one operation.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a6213-105">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="a6213-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a6213-106">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="a6213-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a6213-107">Se este diretório não existir, vá para (página de download) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="a6213-107">If this directory does not exist, go to (download page) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a6213-108">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="a6213-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLActivation`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a6213-109">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="a6213-109">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a6213-110">Abra a solução de XAMLActivation.sln em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a6213-110">Open the XAMLActivation.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="a6213-111">Compile a solução pressionando **F5**.</span><span class="sxs-lookup"><span data-stu-id="a6213-111">Build the solution by pressing **F5**.</span></span>  
  
3.  <span data-ttu-id="a6213-112">Execução WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="a6213-112">Run WcfTestClient.exe.</span></span> <span data-ttu-id="a6213-113">Do prompt de comando, digite o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a6213-113">From a command prompt, type in the following:</span></span>  
  
    1.  <span data-ttu-id="a6213-114">CD %SystemDrive% \ program files \ Microsoft Visual Studio 10.0 \ Common7 \ IDE</span><span class="sxs-lookup"><span data-stu-id="a6213-114">cd %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE</span></span>  
  
    2.  <span data-ttu-id="a6213-115">Execução WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="a6213-115">Run WcfTestClient.exe.</span></span>  
  
4.  <span data-ttu-id="a6213-116">Definir o endereço do serviço em WcfTestClient.exe pressionando CTRL + SHIFT + A e definir o endereço do serviço como http://localhost:56133/Service.xamlx.</span><span class="sxs-lookup"><span data-stu-id="a6213-116">Set the address of the service on WcfTestClient.exe by pressing CTRL+SHIFT+A and setting the service address to http://localhost:56133/Service.xamlx.</span></span>  
  
5.  <span data-ttu-id="a6213-117">Executar a operação de eco para testar o serviço.</span><span class="sxs-lookup"><span data-stu-id="a6213-117">Perform the echo operation to test the service.</span></span>  
  
6.  <span data-ttu-id="a6213-118">Implantar o serviço no IIS usando DeployToIIS.Bat em um prompt de comando com privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="a6213-118">Deploy the Service in IIS using DeployToIIS.Bat in a command prompt with administrator privileges.</span></span>  
  
7.  <span data-ttu-id="a6213-119">Atualize o endereço de serviço no cliente para http://localhost/XAMLActivation/Service.xamlx e testar o serviço novamente usando WcfTestClient.exe.</span><span class="sxs-lookup"><span data-stu-id="a6213-119">Update the service address in the client to http://localhost/XAMLActivation/Service.xamlx and test the service again using WcfTestClient.exe.</span></span>
