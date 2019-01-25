---
title: Solução de problemas do tutorial de introdução
ms.date: 03/30/2017
ms.assetid: 69a21511-0871-4c41-9a53-93110e84d7fd
ms.openlocfilehash: 5b8cd04ef4d98e522e255e1b7529e848351b2e0c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695654"
---
# <a name="troubleshooting-the-getting-started-tutorial"></a><span data-ttu-id="c1653-102">Solução de problemas do tutorial de introdução</span><span class="sxs-lookup"><span data-stu-id="c1653-102">Troubleshooting the Getting Started Tutorial</span></span>
<span data-ttu-id="c1653-103">Este tópico lista os problemas mais comuns encontrados ao trabalhar por meio do Tutorial de Introdução e como resolvê-los.</span><span class="sxs-lookup"><span data-stu-id="c1653-103">This topic lists the most common problems encountered when working through the Getting Started Tutorial and how to resolve them.</span></span>  
  
<span data-ttu-id="c1653-104">**Não consigo localizar os arquivos de projeto no meu disco rígido.**</span><span class="sxs-lookup"><span data-stu-id="c1653-104">**I am unable to find the project files on my hard drive.**</span></span>

 <span data-ttu-id="c1653-105">O Visual Studio salva arquivos de projeto em c:\users\\<user name>\Documents\\< versão do Visual Studio\>\Projects.</span><span class="sxs-lookup"><span data-stu-id="c1653-105">Visual Studio saves project files in c:\users\\<user name>\Documents\\<Visual Studio version\>\Projects.</span></span>  
  
<span data-ttu-id="c1653-106">**A tentativa de executar o aplicativo de serviço: HTTP não foi possível registrar a URL `http://+:8000/ServiceModelSamples/Service/`.** 
 **Seu processo não tem direitos de acesso a esse namespace.**</span><span class="sxs-lookup"><span data-stu-id="c1653-106">**Attempting to run the service application: HTTP could not register URL `http://+:8000/ServiceModelSamples/Service/`.**
**Your process does not have access rights to this namespace.**</span></span> 

 <span data-ttu-id="c1653-107">O processo que hospeda um serviço WCF deve ser executado com privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="c1653-107">The process that hosts a WCF service must be run with Administrative privileges.</span></span> <span data-ttu-id="c1653-108">Se você estiver executando o serviço de dentro do Visual Studio, você deve executar o Visual Studio como administrador.</span><span class="sxs-lookup"><span data-stu-id="c1653-108">If you are running the service from inside Visual Studio, you must run Visual Studio as an Administrator.</span></span> <span data-ttu-id="c1653-109">Para isso, clique em **inicie**, clique com botão direito **Visual Studio \< *versão* >**  e selecione **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="c1653-109">To do so click **Start**, right-click **Visual Studio \<*version*>** and select **Run As Administrator**.</span></span> <span data-ttu-id="c1653-110">Se você estiver executando o serviço em um prompt de linha de comando na janela do console, você deve iniciar a janela do console como um administrador de maneira semelhante.</span><span class="sxs-lookup"><span data-stu-id="c1653-110">If you are running the service from a command-line prompt in a console window, you must start the console window as an Administrator in a similar way.</span></span> <span data-ttu-id="c1653-111">Clique em **inicie**, clique com botão direito **Prompt de comando** e selecione **executar como administrador**.</span><span class="sxs-lookup"><span data-stu-id="c1653-111">Click **Start**, right-click **Command Prompt** and select **Run As Administrator**.</span></span>  
  
<span data-ttu-id="c1653-112">**A tentativa de usar a ferramenta Svcutil.exe: 'svcutil' não é reconhecido como um comando interno ou externo, programa operável ou arquivo em lotes.**</span><span class="sxs-lookup"><span data-stu-id="c1653-112">**Attempting to use the Svcutil.exe tool: 'svcutil' is not recognized as an internal or external command, operable program or batch file.**</span></span>

 <span data-ttu-id="c1653-113">Svcutil.exe deve estar no caminho do sistema.</span><span class="sxs-lookup"><span data-stu-id="c1653-113">Svcutil.exe must be in the system path.</span></span> <span data-ttu-id="c1653-114">A solução mais fácil é usar o Prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="c1653-114">The easiest solution is to use the Command Prompt.</span></span> <span data-ttu-id="c1653-115">Clique em **inicie**, selecione **todos os programas**, **Visual Studio \< *versão*>**,  **Ferramentas do Visual Studio**, e **Prompt de comando do desenvolvedor para Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="c1653-115">Click **Start**, select **All Programs**, **Visual Studio \<*version*>**, **Visual Studio Tools**, and **Developer Command Prompt for Visual Studio**.</span></span> <span data-ttu-id="c1653-116">Esse prompt de comando define o caminho do sistema para os locais corretos para todas as ferramentas que é fornecidas como parte do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c1653-116">This command prompt sets the system path to the correct locations for all tools shipped as part of Visual Studio.</span></span>  

<span data-ttu-id="c1653-117">**Não é possível localizar o arquivo App. config gerado pelo Svcutil.exe.**</span><span class="sxs-lookup"><span data-stu-id="c1653-117">**Unable to find the App.config file generated by Svcutil.exe.**</span></span>

 <span data-ttu-id="c1653-118">O **Add Existing Item** caixa de diálogo exibe somente os arquivos com as seguintes extensões por padrão:. cs,. resx,. Settings,. xsd,. WSDL.</span><span class="sxs-lookup"><span data-stu-id="c1653-118">The **Add Existing Item** dialog only displays files with the following extensions by default: .cs, .resx, .settings, .xsd, .wsdl.</span></span> <span data-ttu-id="c1653-119">Você pode especificar que você deseja ver todos os tipos de arquivo, selecionando **todos os arquivos (\*.\*)**  na caixa de lista suspensa no canto inferior direito do **Add Existing Item** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="c1653-119">You can specify that you want to see all file types by selecting **All Files (\*.\*)** in the drop-down list box in the lower right corner of the **Add Existing Item** dialog box.</span></span>  


<span data-ttu-id="c1653-120">**Compilando o aplicativo cliente: 'CalculatorClient' não contém uma definição para '\<nome do método >' e nenhum método de extensão '\<nome do método >' aceitando um primeiro argumento do tipo 'CalculatorClient' pôde ser encontrado (está faltando um usando diretiva ou um referência de assembly?)**</span><span class="sxs-lookup"><span data-stu-id="c1653-120">**Compiling the client application: 'CalculatorClient' does not contain a definition for '\<method name>' and no extension method '\<method name>' accepting a first argument of type 'CalculatorClient' could be found (are you missing a using directive or an assembly reference?)**</span></span>  

<span data-ttu-id="c1653-121">Somente os métodos que são marcados com o `ServiceOperationAttribute` são expostos para o mundo exterior.</span><span class="sxs-lookup"><span data-stu-id="c1653-121">Only those methods that are marked with the `ServiceOperationAttribute` are exposed to the outside world.</span></span> <span data-ttu-id="c1653-122">Se você omitir a `ServiceOperationAttribute` atributo de um dos métodos a `ICalculator` interface, você receber essa mensagem de erro ao compilar um aplicativo cliente que faz uma chamada para a operação não tem o atributo.</span><span class="sxs-lookup"><span data-stu-id="c1653-122">If you omitted the `ServiceOperationAttribute` attribute from one of the methods in the `ICalculator` interface, you get this error message when compiling a client application that makes a call to the operation missing the attribute.</span></span>  

<span data-ttu-id="c1653-123">**Compilando o aplicativo cliente: O nome do namespace ou tipo 'CalculatorClient' não pôde ser encontrado (está faltando um usando diretiva ou uma referência de assembly?)**</span><span class="sxs-lookup"><span data-stu-id="c1653-123">**Compiling the client application: The type or namespace name 'CalculatorClient' could not be found (are you missing a using directive or an assembly reference?)**</span></span>

 <span data-ttu-id="c1653-124">Você receberá esse erro se você não adicionar o arquivo Proxy.cs ou Proxy.vb ao seu projeto de cliente.</span><span class="sxs-lookup"><span data-stu-id="c1653-124">You get this error if you do not add the Proxy.cs or Proxy.vb file to your client project.</span></span>  

<span data-ttu-id="c1653-125">**Executando o cliente: Exceção sem tratamento: System.ServiceModel.EndpointNotFoundException: Não foi possível conectar ao `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`. Código de erro TCP 10061: Nenhuma conexão pôde ser feita porque a máquina de destino recusou-a ativamente.**</span><span class="sxs-lookup"><span data-stu-id="c1653-125">**Running the client: Unhandled Exception: System.ServiceModel.EndpointNotFoundException: Could not connect to `http://localhost:8000/ServiceModelSamples/Service/CalculatorService`. TCP error code 10061: No connection could be made because the target machine actively refused it.**</span></span>

<span data-ttu-id="c1653-126">Esse erro ocorre se você executar o aplicativo cliente sem executar o serviço.</span><span class="sxs-lookup"><span data-stu-id="c1653-126">This error occurs if you run the client application without running the service.</span></span>  
  
<span data-ttu-id="c1653-127">**Exceção sem tratamento: System.ServiceModel.Security.SecurityNegotiationException: Negociação de segurança SOAP com `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` de destino `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` falhou**</span><span class="sxs-lookup"><span data-stu-id="c1653-127">**Unhandled Exception: System.ServiceModel.Security.SecurityNegotiationException: SOAP security negotiation with `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` for target `http://localhost:8000/ServiceModelSamples/Service/CalculatorService` failed**</span></span>  

<span data-ttu-id="c1653-128">Esse erro ocorre em um computador ingressado no domínio que não tem conectividade de rede.</span><span class="sxs-lookup"><span data-stu-id="c1653-128">This error occurs on a domain-joined computer that does not have network connectivity.</span></span> <span data-ttu-id="c1653-129">Conectar seu computador à rede ou desativar a segurança para o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="c1653-129">Either connect your computer to the network or turn off security for both the client and the service.</span></span> <span data-ttu-id="c1653-130">Para o serviço, modifique o código que cria o WSHttpBinding ao seguinte.</span><span class="sxs-lookup"><span data-stu-id="c1653-130">For the service, modify the code that creates the WSHttpBinding to the following.</span></span>  
  
```csharp
// Step 3 of the hosting procedure: Add a service endpoint  
selfhost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(SecurityMode.None), "CalculatorService");  
```

<span data-ttu-id="c1653-131">Para o cliente, altere o  **\<segurança >** elemento sob o  **\<associação >** elemento para o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c1653-131">For the client, change the **\<security>** element under the **\<binding>** element to the following:</span></span>  
  
```xml
<security mode="Node" />  
```  

## <a name="see-also"></a><span data-ttu-id="c1653-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1653-132">See also</span></span>
- [<span data-ttu-id="c1653-133">Tutorial de Introdução</span><span class="sxs-lookup"><span data-stu-id="c1653-133">Getting Started Tutorial</span></span>](../../../docs/framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="c1653-134">Início rápido de solução de problemas do WCF</span><span class="sxs-lookup"><span data-stu-id="c1653-134">WCF Troubleshooting Quickstart</span></span>](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)
- [<span data-ttu-id="c1653-135">Solução de problemas de instalação</span><span class="sxs-lookup"><span data-stu-id="c1653-135">Troubleshooting Setup Issues</span></span>](../../../docs/framework/wcf/troubleshooting-setup-issues.md)
