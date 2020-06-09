---
title: LeiaMe para exemplo de autenticação de proteção estendida
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
ms.openlocfilehash: 9b0a3535282a1fcc1103651f5601459e80d3d8d4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601095"
---
# <a name="readme-for-extended-protection-authentication-sample"></a><span data-ttu-id="e3fb3-102">LeiaMe para exemplo de autenticação de proteção estendida</span><span class="sxs-lookup"><span data-stu-id="e3fb3-102">ReadMe for Extended Protection Authentication Sample</span></span>

<span data-ttu-id="e3fb3-103">A proteção estendida é uma iniciativa de segurança para proteger contra ataques MITM (Man-in-the-Middle), em que um invasor (o "Man-in-the-middle") intercepta as credenciais de um cliente e as usa para acessar recursos seguros no servidor pretendido do cliente.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-103">Extended Protection is a security initiative to protect against man-in-the-middle (MITM) attacks, in which an attacker (the "man-in-the-middle") intercepts a client’s credentials and uses them to access secure resources on the client’s intended server.</span></span>

<span data-ttu-id="e3fb3-104">Para obter mais informações, consulte [proteção estendida para autenticação visão geral](extended-protection-for-authentication-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e3fb3-104">For more information, see [Extended Protection for Authentication Overview](extended-protection-for-authentication-overview.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e3fb3-105">Este exemplo só funciona quando hospedado no IIS.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-105">This sample only works when hosted on IIS.</span></span> <span data-ttu-id="e3fb3-106">Ele não funciona em Visual Studio Development Server porque isso não oferece suporte a HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-106">It does not work on Visual Studio Development Server because that does not support HTTPS.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e3fb3-107">Para configurar, compilar e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="e3fb3-107">To Set Up, Build, and Run the Sample</span></span>

1. <span data-ttu-id="e3fb3-108">Instale o IIS no computador por meio de adicionar/remover programas-> recursos do Windows.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-108">Install IIS on the machine from Add/Remove Programs -> Windows Features.</span></span>

2. <span data-ttu-id="e3fb3-109">Ative a autenticação do Windows em recursos do Windows: Serviços de Informações da Internet-> serviços de World Wide Web-> segurança-> autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-109">Turn on Windows Authentication in Windows features: Internet Information Services -> World Wide Web Services -> Security -> Windows Authentication.</span></span>

3. <span data-ttu-id="e3fb3-110">Ative a ativação HTTP nos recursos do Windows: Microsoft .NET Framework 3.5.1-> Windows Communication Foundation ativação HTTP.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-110">Turn on HTTP Activation in Windows features: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP Activation.</span></span>

4. <span data-ttu-id="e3fb3-111">Este exemplo requer que o cliente estabeleça um canal seguro com o servidor e, por isso, ele requer a presença de um certificado de servidor que pode ser instalado no Gerenciador Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="e3fb3-111">This sample requires the client to establish a secure channel with the server and so it requires the presence of a server certificate which can be installed from Internet Information Services (IIS) Manager.</span></span>

    1. <span data-ttu-id="e3fb3-112">Abra o Gerenciador do IIS-> certificados do servidor (na guia exibição de recurso).</span><span class="sxs-lookup"><span data-stu-id="e3fb3-112">Open the IIS manager -> Server certificates (from the feature view tab).</span></span>

    2. <span data-ttu-id="e3fb3-113">Para testar esse exemplo, você pode criar um certificado autoassinado.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-113">For the purpose of testing this sample, you can create a self-signed certificate.</span></span> <span data-ttu-id="e3fb3-114">(Se você não quiser que o Internet Explorer solicite que o certificado não seja seguro, você poderá instalá-lo no repositório de autoridade raiz do certificado confiável).</span><span class="sxs-lookup"><span data-stu-id="e3fb3-114">(If you don’t want Internet Explorer to prompt you about the certificate not being secure, you can install it in the Trusted Certificate Root authority store).</span></span>

5. <span data-ttu-id="e3fb3-115">Vá para o painel Ações do site da Web padrão.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-115">Go to the Actions pane for the Default Web site.</span></span> <span data-ttu-id="e3fb3-116">Clique em Editar associações de > de site.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-116">Click Edit Site -> Bindings.</span></span> <span data-ttu-id="e3fb3-117">Adicione HTTPS como um tipo se ele ainda não estiver presente, com o número da porta 443 e atribua o certificado SSL criado na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-117">Add HTTPS as a type if it is not already present, with port number 443, and assign the SSL certificate created in the above step.</span></span>

6. <span data-ttu-id="e3fb3-118">Crie o serviço.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-118">Build the service.</span></span> <span data-ttu-id="e3fb3-119">Isso cria um diretório virtual no IIS para você (a partir da ação de Build especificada nas propriedades do projeto) e copia os arquivos dll,. svc e config conforme necessário para que um serviço seja hospedado na Web.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-119">This creates a virtual directory in IIS for you (from the post build action specified in the project properties) and copies the dll, .svc and config files as needed for a service to be Web hosted.</span></span>

7. <span data-ttu-id="e3fb3-120">Abra o Gerenciador do IIS.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-120">Open the IIS Manager.</span></span> <span data-ttu-id="e3fb3-121">Clique com o botão direito do mouse no diretório virtual (ExtendedProtection) que você criou na etapa anterior e selecione converter para aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-121">Right-click the virtual directory (ExtendedProtection) that you created in the previous step and select Convert to Application.</span></span>

8. <span data-ttu-id="e3fb3-122">Abra o módulo de autenticação no Gerenciador do IIS para este diretório virtual e habilite a autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-122">Open the Authentication module in IIS Manager for this virtual directory and enable Windows Authentication.</span></span>

9. <span data-ttu-id="e3fb3-123">Abra as configurações avançadas para autenticação do Windows para este diretório virtual e defina-o como obrigatório, já que, no exemplo, a configuração ExtendedProtection correspondente é definida como Always.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-123">Open the Advanced Settings for Windows Authentication for this virtual directory and set it to Required, since, in the sample, the corresponding ExtendedProtection setting is set to Always.</span></span>

10. <span data-ttu-id="e3fb3-124">Você pode testar o serviço acessando a URL em uma janela do navegador.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-124">You can test the service by accessing the URL from a browser window.</span></span> <span data-ttu-id="e3fb3-125">Se você quiser acessar essa URL de um computador cruzado, certifique-se de que o firewall esteja aberto para todas as conexões HTTP e HTTPS de entrada.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-125">If you want to access this URL from a cross machine, make sure that the firewall is opened for all incoming HTTP and HTTPS connections.</span></span>

11. <span data-ttu-id="e3fb3-126">Abra o arquivo de configuração do cliente e forneça um nome de máquina completo para o \<client>  -  \<endpoint> atributo-address, substituindo \<full_machine_name> .</span><span class="sxs-lookup"><span data-stu-id="e3fb3-126">Open the client config file and provide a full machine name for the \<client> - \<endpoint> - address attribute, replacing \<full_machine_name>.</span></span>

12. <span data-ttu-id="e3fb3-127">Execute o cliente.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-127">Run the client.</span></span> <span data-ttu-id="e3fb3-128">O cliente se comunica com o serviço estabelecendo um canal seguro e usando a proteção estendida nos bastidores.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-128">The client communicates to the service by establishing a secure channel and using extended protection under the covers.</span></span>
