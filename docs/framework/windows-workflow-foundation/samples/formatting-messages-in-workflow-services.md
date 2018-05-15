---
title: Mensagens de formatação em serviços de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
ms.openlocfilehash: eac9f7042dbcbd31f9a8c7d5e56c7b7d2ab62156
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="formatting-messages-in-workflow-services"></a><span data-ttu-id="b9c0f-102">Mensagens de formatação em serviços de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="b9c0f-102">Formatting messages in Workflow Services</span></span>
<span data-ttu-id="b9c0f-103">Este exemplo mostra como os tipos de usuário diferentes podem ser usados em atividades de mensagem (de serviços WCF).</span><span class="sxs-lookup"><span data-stu-id="b9c0f-103">This sample shows how different user types can be used in messaging activities (WF services).</span></span> <span data-ttu-id="b9c0f-104">O serviço de exemplo é um serviço simples de aprovação de despesas e expõe três operações.</span><span class="sxs-lookup"><span data-stu-id="b9c0f-104">The sample service is a simple expense approval service and exposes three operations.</span></span> <span data-ttu-id="b9c0f-105">`ApproveExpense` utiliza um tipo de contrato de dados e mostra como usar tipos conhecidos.</span><span class="sxs-lookup"><span data-stu-id="b9c0f-105">`ApproveExpense` takes a data contract type and shows how to use known types.</span></span> <span data-ttu-id="b9c0f-106">Retorna `true` ou `false` da operação com base na quantidade de despesas.</span><span class="sxs-lookup"><span data-stu-id="b9c0f-106">The operation returns `true` or `false` based on the expense amount.</span></span> <span data-ttu-id="b9c0f-107">`ApprovePO` usa um tipo de XmlSerializer e retorna `true` ou `false` com base no valor de despesas.`ApprovedVendor`</span><span class="sxs-lookup"><span data-stu-id="b9c0f-107">`ApprovePO` takes an XmlSerializer type and returns `true` or `false` based on the expense amount.`ApprovedVendor`</span></span> <span data-ttu-id="b9c0f-108">usa um tipo de contrato de mensagem e retorna `true` ou `false` se ele estiver na lista de fornecedores aprovados ou se originou a solicitação do departamento de Finanças (o departamento financeiro pode usar qualquer fornecedor).</span><span class="sxs-lookup"><span data-stu-id="b9c0f-108">takes a message contract type and returns `true` or `false` if the vendor is in the list of approved vendors or if the request came from the finance department (the finance department can use any vendor).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="b9c0f-109">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="b9c0f-109">To use this sample</span></span>  
  
1.  <span data-ttu-id="b9c0f-110">Carregar a solução do projeto em [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] e compile o projeto.</span><span class="sxs-lookup"><span data-stu-id="b9c0f-110">Load the project solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and build the project.</span></span>  
  
2.  <span data-ttu-id="b9c0f-111">Executa serviço, gerado em [] do diretório da solução FormatterService \ \ bin \ debug \\</span><span class="sxs-lookup"><span data-stu-id="b9c0f-111">First run the service, generated in [solution base directory]\FormatterService\bin\debug\\</span></span>  
  
3.  <span data-ttu-id="b9c0f-112">Segundo, executa aplicativo cliente gerado em [] do diretório da solução FormatterClient \ \ bin \ debug.</span><span class="sxs-lookup"><span data-stu-id="b9c0f-112">Second, run the Client application generated in [solution base directory]\FormatterClient\bin\debug.</span></span>  
  
4.  <span data-ttu-id="b9c0f-113">O cliente chama três operações no serviço e imprime os resultados.</span><span class="sxs-lookup"><span data-stu-id="b9c0f-113">The client calls three operations on the service and prints the results.</span></span> <span data-ttu-id="b9c0f-114">Quando completo, pressione ENTER para sair do cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="b9c0f-114">When complete, press ENTER to exit the client and then the service.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b9c0f-115">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="b9c0f-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b9c0f-116">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="b9c0f-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b9c0f-117">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="b9c0f-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b9c0f-118">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="b9c0f-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`