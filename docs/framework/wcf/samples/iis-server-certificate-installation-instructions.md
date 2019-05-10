---
title: Instruções da instalação do certificado de servidor dos Serviços de Informações da Internet (IIS)
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: 728232c4e1d6309ae0cfacb407417173ece145da
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648357"
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a><span data-ttu-id="df720-102">Instruções da instalação do certificado de servidor dos Serviços de Informações da Internet (IIS)</span><span class="sxs-lookup"><span data-stu-id="df720-102">Internet Information Services (IIS) Server Certificate Installation Instructions</span></span>
<span data-ttu-id="df720-103">Para executar os exemplos que comunicam com segurança com o IIS (Serviços de Informações da Internet), você deverá criar e instalar um certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="df720-103">To run the samples that securely communicate with Internet Information Services (IIS), you must create and install a server certificate.</span></span>  
  
## <a name="step-1-creating-certificates"></a><span data-ttu-id="df720-104">Etapa 1.</span><span class="sxs-lookup"><span data-stu-id="df720-104">Step 1.</span></span> <span data-ttu-id="df720-105">Criando certificados</span><span class="sxs-lookup"><span data-stu-id="df720-105">Creating Certificates</span></span>  
 <span data-ttu-id="df720-106">Para criar um certificado para seu computador, abra um Prompt de comando do desenvolvedor para Visual Studio com privilégios de administrador e execute o Setup. bat que está incluído em cada um dos exemplos que usam a comunicação segura com o IIS.</span><span class="sxs-lookup"><span data-stu-id="df720-106">To create a certificate for your computer, open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat that is included in each of the samples that use secure communication with IIS.</span></span> <span data-ttu-id="df720-107">Verifique se o caminho inclui a pasta que contém Makecert.exe antes de executar este arquivo em lote.</span><span class="sxs-lookup"><span data-stu-id="df720-107">Ensure that the path includes the folder that contains Makecert.exe before you run this batch file.</span></span> <span data-ttu-id="df720-108">O comando a seguir é usado para criar o certificado em Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="df720-108">The following command is used to create the certificate in Setup.bat.</span></span>  
  
```  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a><span data-ttu-id="df720-109">Etapa 2.</span><span class="sxs-lookup"><span data-stu-id="df720-109">Step 2.</span></span> <span data-ttu-id="df720-110">Instalando certificados</span><span class="sxs-lookup"><span data-stu-id="df720-110">Installing Certificates</span></span>  
 <span data-ttu-id="df720-111">As etapas necessárias para instalar os certificados que você criou dependem de qual versão do IIS você está usando.</span><span class="sxs-lookup"><span data-stu-id="df720-111">The steps required to install the certificates you just created depend on which version of IIS you are using.</span></span>  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a><span data-ttu-id="df720-112">Para instalar o IIS no IIS 5.1 (Windows XP) e IIS 6.0 (Windows Server 2003)</span><span class="sxs-lookup"><span data-stu-id="df720-112">To install IIS on IIS 5.1 (Windows XP) and IIS 6.0 (Windows Server 2003)</span></span>  
  
1. <span data-ttu-id="df720-113">Abra o snap-in do MMC do Gerenciador dos Serviços de Informações da Internet.</span><span class="sxs-lookup"><span data-stu-id="df720-113">Open the Internet Information Services Manager MMC Snap-In.</span></span>  
  
2. <span data-ttu-id="df720-114">O site padrão com o botão direito e selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="df720-114">Right-click the default Web site and select **Properties**.</span></span>  
  
3. <span data-ttu-id="df720-115">Selecione o **segurança de diretório** guia.</span><span class="sxs-lookup"><span data-stu-id="df720-115">Select the **Directory Security** tab.</span></span>  
  
4. <span data-ttu-id="df720-116">Clique o **certificado do servidor** botão.</span><span class="sxs-lookup"><span data-stu-id="df720-116">Click the **Server Certificate** button.</span></span> <span data-ttu-id="df720-117">O assistente de certificado do servidor Web é iniciado.</span><span class="sxs-lookup"><span data-stu-id="df720-117">The Web Server Certificate Wizard starts.</span></span>  
  
5. <span data-ttu-id="df720-118">Conclua o assistente.</span><span class="sxs-lookup"><span data-stu-id="df720-118">Complete the wizard.</span></span> <span data-ttu-id="df720-119">Selecione a opção para atribuir um certificado.</span><span class="sxs-lookup"><span data-stu-id="df720-119">Select the option to assign a certificate.</span></span> <span data-ttu-id="df720-120">Selecione o certificado ServiceModelSamples-HTTPS-Server da lista de certificados que são exibidos.</span><span class="sxs-lookup"><span data-stu-id="df720-120">Select the ServiceModelSamples-HTTPS-Server certificate from the list of certificates that are displayed.</span></span>  
  
     <span data-ttu-id="df720-121">![Assistente de certificado do IIS](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span><span class="sxs-lookup"><span data-stu-id="df720-121">![IIS Certificate Wizard](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span></span>  
  
6. <span data-ttu-id="df720-122">Testar o acesso ao serviço em um navegador usando o endereço HTTPS `https://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="df720-122">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a><span data-ttu-id="df720-123">Se o SSL foi configurado anteriormente usando Httpcfg.exe</span><span class="sxs-lookup"><span data-stu-id="df720-123">If SSL was previously configured by using Httpcfg.exe</span></span>  
  
1. <span data-ttu-id="df720-124">Use Makecert.exe (ou execute Setup.bat) para criar o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="df720-124">Use Makecert.exe (or run Setup.bat) to create the server certificate.</span></span>  
  
2. <span data-ttu-id="df720-125">Execute o Gerenciador do IIS e instale o certificado de acordo com as etapas anteriores.</span><span class="sxs-lookup"><span data-stu-id="df720-125">Run the IIS manager and install the certificate according to the previous steps.</span></span>  
  
3. <span data-ttu-id="df720-126">Adicione a seguinte linha de código ao programa cliente.</span><span class="sxs-lookup"><span data-stu-id="df720-126">Add the following line of code to the client program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="df720-127">Esse código somente é necessário para certificados de teste como os criados por Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="df720-127">This code is only required for test certificates such as those created by Makecert.exe.</span></span> <span data-ttu-id="df720-128">Não é recomendável para o código de produção.</span><span class="sxs-lookup"><span data-stu-id="df720-128">It is not recommended for production code.</span></span>  
  
```  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a><span data-ttu-id="df720-129">Para instalar o IIS no IIS 7.0 (Windows Vista e Windows Server 2008)</span><span class="sxs-lookup"><span data-stu-id="df720-129">To install IIS on IIS 7.0 (Windows Vista and Windows Server 2008)</span></span>  
  
1. <span data-ttu-id="df720-130">Do **iniciar** menu, clique em **execute**, em seguida, digite **inetmgr** para abrir o snap-in MMC de serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="df720-130">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="df720-131">Clique com botão direito do **Site padrão** e selecione **Editar Ligações...**</span><span class="sxs-lookup"><span data-stu-id="df720-131">Right-click the **Default Web Site** and select **Edit Bindings…**</span></span>  
  
3. <span data-ttu-id="df720-132">Clique o **Add** botão da **associações de Site** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="df720-132">Click the **Add** button of the **Site Bindings** dialog box.</span></span>  
  
4. <span data-ttu-id="df720-133">Selecione **HTTPS** da **tipo** lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="df720-133">Select **HTTPS** from the **Type** drop-down list.</span></span>  
  
5. <span data-ttu-id="df720-134">Selecione o **ServiceModelSamples-HTTPS-Server** da **certificado SSL** lista suspensa e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="df720-134">Select the **ServiceModelSamples-HTTPS-Server** from the **SSL certificate** drop-down list and click **OK**.</span></span>  
  
6. <span data-ttu-id="df720-135">Testar o acesso ao serviço em um navegador usando o endereço HTTPS `https://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="df720-135">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df720-136">Como o certificado de teste que você acabou de instalar não é um certificado confiável, você poderá encontrar avisos de segurança adicionais do Internet Explorer ao navegar em endereços Web locais protegidos por esse certificado.</span><span class="sxs-lookup"><span data-stu-id="df720-136">Because the test certificate you have just installed is not a trusted certificate, you may encounter additional Internet Explorer security warnings when browsing to local Web addresses secured with this certificate.</span></span>  
  
## <a name="removing-certificates"></a><span data-ttu-id="df720-137">Removendo certificados</span><span class="sxs-lookup"><span data-stu-id="df720-137">Removing Certificates</span></span>  
  
- <span data-ttu-id="df720-138">Use o Gerenciador dos Serviços de Informações da Internet como direcionado anteriormente, mas remova o certificado ou associação em vez de adicionar.</span><span class="sxs-lookup"><span data-stu-id="df720-138">Use the Internet Information Services Manager as previously directed, but remove the certificate or binding instead of adding it.</span></span>  
  
- <span data-ttu-id="df720-139">Remova o certificado do computador usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="df720-139">Remove the computer certificate by using the following command.</span></span>  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
