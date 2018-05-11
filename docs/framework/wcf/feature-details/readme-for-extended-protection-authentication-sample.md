---
title: LeiaMe para exemplo de autenticação de proteção estendida
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d45271180b7f00ba78d106f2a93d5860375da5f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="readme-for-extended-protection-authentication-sample"></a><span data-ttu-id="1c56a-102">LeiaMe para exemplo de autenticação de proteção estendida</span><span class="sxs-lookup"><span data-stu-id="1c56a-102">ReadMe for Extended Protection Authentication Sample</span></span>
<span data-ttu-id="1c56a-103">Proteção estendida é uma iniciativa de segurança para impedir ataques man-in-the-middle (MITM), em que um invasor (o "man-in-the-middle") intercepta as credenciais do cliente e as utiliza para acessar recursos protegidos no servidor pretendido do cliente.</span><span class="sxs-lookup"><span data-stu-id="1c56a-103">Extended Protection is a security initiative to protect against man-in-the-middle (MITM) attacks, in which an attacker (the "man-in-the-middle") intercepts a client’s credentials and uses them to access secure resources on the client’s intended server.</span></span>  
  
 <span data-ttu-id="1c56a-104">Para obter mais informações, consulte [proteção estendida para visão geral da autenticação](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1c56a-104">For more information, see [Extended Protection for Authentication Overview](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c56a-105">Este exemplo só funciona quando hospedados no IIS.</span><span class="sxs-lookup"><span data-stu-id="1c56a-105">This sample only works when hosted on IIS.</span></span> <span data-ttu-id="1c56a-106">Ele não funciona no servidor de desenvolvimento do Visual Studio porque que não oferece suporte a HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1c56a-106">It does not work on Visual Studio Development Server because that does not support HTTPS.</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1c56a-107">Para configurar, compilar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="1c56a-107">To Set Up, Build, and Run the Sample</span></span>  
  
1.  <span data-ttu-id="1c56a-108">Instale o IIS no computador de adicionar ou remover programas -> recursos do Windows.</span><span class="sxs-lookup"><span data-stu-id="1c56a-108">Install IIS on the machine from Add/Remove Programs -> Windows Features.</span></span>  
  
2.  <span data-ttu-id="1c56a-109">Ativar a autenticação do Windows em recursos do Windows: serviços de informações da Internet -> Serviços da World Wide Web -> Segurança -> autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="1c56a-109">Turn on Windows Authentication in Windows features: Internet Information Services -> World Wide Web Services -> Security -> Windows Authentication.</span></span>  
  
3.  <span data-ttu-id="1c56a-110">Ativar a ativação HTTP nos recursos do Windows: Microsoft .NET Framework 3.5.1 -> Ativação HTTP do Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="1c56a-110">Turn on HTTP Activation in Windows features: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP Activation.</span></span>  
  
4.  <span data-ttu-id="1c56a-111">Este exemplo requer que o cliente estabelecer um canal seguro com o servidor e então exige a presença de um certificado de servidor que pode ser instalado do Gerenciador de serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="1c56a-111">This sample requires the client to establish a secure channel with the server and so it requires the presence of a server certificate which can be installed from Internet Information Services (IIS) Manager.</span></span>  
  
    1.  <span data-ttu-id="1c56a-112">Abra o Gerenciador do IIS -> certificados do servidor (a partir da guia de exibição de recurso).</span><span class="sxs-lookup"><span data-stu-id="1c56a-112">Open the IIS manager -> Server certificates (from the feature view tab).</span></span>  
  
    2.  <span data-ttu-id="1c56a-113">Com a finalidade de testar este exemplo, você pode criar um certificado autoassinado.</span><span class="sxs-lookup"><span data-stu-id="1c56a-113">For the purpose of testing this sample, you can create a self-signed certificate.</span></span> <span data-ttu-id="1c56a-114">(Se você não quiser o Internet Explorer para solicitar que você sobre o certificado não está sendo seguro, você pode instalá-lo no repositório de autoridade de certificado de raiz confiável).</span><span class="sxs-lookup"><span data-stu-id="1c56a-114">(If you don’t want Internet Explorer to prompt you about the certificate not being secure, you can install it in the Trusted Certificate Root authority store).</span></span>  
  
5.  <span data-ttu-id="1c56a-115">Vá para o painel de ações para o site da Web padrão.</span><span class="sxs-lookup"><span data-stu-id="1c56a-115">Go to the Actions pane for the Default Web site.</span></span> <span data-ttu-id="1c56a-116">Clique em Editar Site -> associações.</span><span class="sxs-lookup"><span data-stu-id="1c56a-116">Click Edit Site -> Bindings.</span></span> <span data-ttu-id="1c56a-117">Adicione HTTPS como um tipo se ele não ainda estiver presente, com o número da porta 443 e atribui o certificado SSL criado na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="1c56a-117">Add HTTPS as a type if it is not already present, with port number 443, and assign the SSL certificate created in the above step.</span></span>  
  
6.  <span data-ttu-id="1c56a-118">O serviço de compilação.</span><span class="sxs-lookup"><span data-stu-id="1c56a-118">Build the service.</span></span> <span data-ttu-id="1c56a-119">Isso cria um diretório virtual no IIS para você (da ação de compilação post especificada nas propriedades do projeto) e copia os arquivos de dll,. svc e configuração conforme necessário para um serviço ser hospedado na Web.</span><span class="sxs-lookup"><span data-stu-id="1c56a-119">This creates a virtual directory in IIS for you (from the post build action specified in the project properties) and copies the dll, .svc and config files as needed for a service to be Web hosted.</span></span>  
  
7.  <span data-ttu-id="1c56a-120">Abra o Gerenciador do IIS.</span><span class="sxs-lookup"><span data-stu-id="1c56a-120">Open the IIS Manager.</span></span> <span data-ttu-id="1c56a-121">O diretório virtual (ExtendedProtection) que você criou na etapa anterior e selecione Converter em aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1c56a-121">Right-click the virtual directory (ExtendedProtection) that you created in the previous step and select Convert to Application.</span></span>  
  
8.  <span data-ttu-id="1c56a-122">Abra o módulo de autenticação no Gerenciador do IIS para este diretório virtual e habilite a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="1c56a-122">Open the Authentication module in IIS Manager for this virtual directory and enable Windows Authentication.</span></span>  
  
9. <span data-ttu-id="1c56a-123">Abra o Advanced configurações de autenticação do Windows para este diretório virtual e defina-a como necessária, como, por exemplo, a configuração de ExtendedProtection correspondente é definida como Always.</span><span class="sxs-lookup"><span data-stu-id="1c56a-123">Open the Advanced Settings for Windows Authentication for this virtual directory and set it to Required, since, in the sample, the corresponding ExtendedProtection setting is set to Always.</span></span>  
  
10. <span data-ttu-id="1c56a-124">Você pode testar o serviço acessando a URL de uma janela do navegador.</span><span class="sxs-lookup"><span data-stu-id="1c56a-124">You can test the service by accessing the URL from a browser window.</span></span> <span data-ttu-id="1c56a-125">Se você quiser acessar essa URL de uma máquina cruzada, certifique-se de que o firewall está aberto todas as conexões de entrada HTTP e HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1c56a-125">If you want to access this URL from a cross machine, make sure that the firewall is opened for all incoming HTTP and HTTPS connections.</span></span>  
  
11. <span data-ttu-id="1c56a-126">Abra o arquivo de configuração do cliente e forneça um nome de computador completo para o \<cliente >- \<ponto de extremidade >-atributo de endereço, substituindo << full_machine_name >>.</span><span class="sxs-lookup"><span data-stu-id="1c56a-126">Open the client config file and provide a full machine name for the \<client> - \<endpoint> - address attribute, replacing <<full_machine_name>>.</span></span>  
  
12. <span data-ttu-id="1c56a-127">Execute o cliente.</span><span class="sxs-lookup"><span data-stu-id="1c56a-127">Run the client.</span></span> <span data-ttu-id="1c56a-128">O cliente se comunica com o serviço de estabelecer um canal seguro e usando proteção estendida nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="1c56a-128">The client communicates to the service by establishing a secure channel and using extended protection under the covers.</span></span>
