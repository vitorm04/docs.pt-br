---
title: Instruções da instalação do certificado de servidor dos Serviços de Informações da Internet (IIS)
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: a89d907b9be25c83a74f0c5d60d184637552f297
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221096"
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a><span data-ttu-id="5dffb-102">Instruções da instalação do certificado de servidor dos Serviços de Informações da Internet (IIS)</span><span class="sxs-lookup"><span data-stu-id="5dffb-102">Internet Information Services (IIS) Server Certificate Installation Instructions</span></span>
<span data-ttu-id="5dffb-103">Para executar os exemplos que comunicam com segurança com o IIS (Serviços de Informações da Internet), você deverá criar e instalar um certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="5dffb-103">To run the samples that securely communicate with Internet Information Services (IIS), you must create and install a server certificate.</span></span>  
  
## <a name="step-1-creating-certificates"></a><span data-ttu-id="5dffb-104">Etapa 1.</span><span class="sxs-lookup"><span data-stu-id="5dffb-104">Step 1.</span></span> <span data-ttu-id="5dffb-105">Criando certificados</span><span class="sxs-lookup"><span data-stu-id="5dffb-105">Creating Certificates</span></span>  
 <span data-ttu-id="5dffb-106">Para criar um certificado para seu computador, abra um Prompt de comando do desenvolvedor para Visual Studio com privilégios de administrador e execute o Setup. bat que está incluído em cada um dos exemplos que usam a comunicação segura com o IIS.</span><span class="sxs-lookup"><span data-stu-id="5dffb-106">To create a certificate for your computer, open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat that is included in each of the samples that use secure communication with IIS.</span></span> <span data-ttu-id="5dffb-107">Verifique se o caminho inclui a pasta que contém Makecert.exe antes de executar este arquivo em lote.</span><span class="sxs-lookup"><span data-stu-id="5dffb-107">Ensure that the path includes the folder that contains Makecert.exe before you run this batch file.</span></span> <span data-ttu-id="5dffb-108">O comando a seguir é usado para criar o certificado em Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="5dffb-108">The following command is used to create the certificate in Setup.bat.</span></span>  
  
```  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a><span data-ttu-id="5dffb-109">Etapa 2.</span><span class="sxs-lookup"><span data-stu-id="5dffb-109">Step 2.</span></span> <span data-ttu-id="5dffb-110">Instalando certificados</span><span class="sxs-lookup"><span data-stu-id="5dffb-110">Installing Certificates</span></span>  
 <span data-ttu-id="5dffb-111">As etapas necessárias para instalar os certificados que você criou dependem de qual versão do IIS você está usando.</span><span class="sxs-lookup"><span data-stu-id="5dffb-111">The steps required to install the certificates you just created depend on which version of IIS you are using.</span></span>  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a><span data-ttu-id="5dffb-112">Para instalar o IIS no IIS 5.1 (Windows XP) e IIS 6.0 (Windows Server 2003)</span><span class="sxs-lookup"><span data-stu-id="5dffb-112">To install IIS on IIS 5.1 (Windows XP) and IIS 6.0 (Windows Server 2003)</span></span>  
  
1.  <span data-ttu-id="5dffb-113">Abra o snap-in do MMC do Gerenciador dos Serviços de Informações da Internet.</span><span class="sxs-lookup"><span data-stu-id="5dffb-113">Open the Internet Information Services Manager MMC Snap-In.</span></span>  
  
2.  <span data-ttu-id="5dffb-114">O site padrão com o botão direito e selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5dffb-114">Right-click the default Web site and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="5dffb-115">Selecione o **segurança de diretório** guia.</span><span class="sxs-lookup"><span data-stu-id="5dffb-115">Select the **Directory Security** tab.</span></span>  
  
4.  <span data-ttu-id="5dffb-116">Clique o **certificado do servidor** botão.</span><span class="sxs-lookup"><span data-stu-id="5dffb-116">Click the **Server Certificate** button.</span></span> <span data-ttu-id="5dffb-117">O assistente de certificado do servidor Web é iniciado.</span><span class="sxs-lookup"><span data-stu-id="5dffb-117">The Web Server Certificate Wizard starts.</span></span>  
  
5.  <span data-ttu-id="5dffb-118">Conclua o assistente.</span><span class="sxs-lookup"><span data-stu-id="5dffb-118">Complete the wizard.</span></span> <span data-ttu-id="5dffb-119">Selecione a opção para atribuir um certificado.</span><span class="sxs-lookup"><span data-stu-id="5dffb-119">Select the option to assign a certificate.</span></span> <span data-ttu-id="5dffb-120">Selecione o certificado ServiceModelSamples-HTTPS-Server da lista de certificados que são exibidos.</span><span class="sxs-lookup"><span data-stu-id="5dffb-120">Select the ServiceModelSamples-HTTPS-Server certificate from the list of certificates that are displayed.</span></span>  
  
     <span data-ttu-id="5dffb-121">![Assistente de certificado do IIS](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span><span class="sxs-lookup"><span data-stu-id="5dffb-121">![IIS Certificate Wizard](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span></span>  
  
6.  <span data-ttu-id="5dffb-122">Testar o acesso ao serviço em um navegador usando o endereço HTTPS `https://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="5dffb-122">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a><span data-ttu-id="5dffb-123">Se o SSL foi configurado anteriormente usando Httpcfg.exe</span><span class="sxs-lookup"><span data-stu-id="5dffb-123">If SSL was previously configured by using Httpcfg.exe</span></span>  
  
1.  <span data-ttu-id="5dffb-124">Use Makecert.exe (ou execute Setup.bat) para criar o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="5dffb-124">Use Makecert.exe (or run Setup.bat) to create the server certificate.</span></span>  
  
2.  <span data-ttu-id="5dffb-125">Execute o Gerenciador do IIS e instale o certificado de acordo com as etapas anteriores.</span><span class="sxs-lookup"><span data-stu-id="5dffb-125">Run the IIS manager and install the certificate according to the previous steps.</span></span>  
  
3.  <span data-ttu-id="5dffb-126">Adicione a seguinte linha de código ao programa cliente.</span><span class="sxs-lookup"><span data-stu-id="5dffb-126">Add the following line of code to the client program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5dffb-127">Esse código somente é necessário para certificados de teste como os criados por Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="5dffb-127">This code is only required for test certificates such as those created by Makecert.exe.</span></span> <span data-ttu-id="5dffb-128">Não é recomendável para o código de produção.</span><span class="sxs-lookup"><span data-stu-id="5dffb-128">It is not recommended for production code.</span></span>  
  
```  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a><span data-ttu-id="5dffb-129">Para instalar o IIS no IIS 7.0 (Windows Vista e Windows Server 2008)</span><span class="sxs-lookup"><span data-stu-id="5dffb-129">To install IIS on IIS 7.0 (Windows Vista and Windows Server 2008)</span></span>  
  
1.  <span data-ttu-id="5dffb-130">Do **iniciar** menu, clique em **execute**, em seguida, digite **inetmgr** para abrir o snap-in MMC de serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="5dffb-130">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2.  <span data-ttu-id="5dffb-131">Clique com botão direito do **Site padrão** e selecione **Editar Ligações...**</span><span class="sxs-lookup"><span data-stu-id="5dffb-131">Right-click the **Default Web Site** and select **Edit Bindings…**</span></span>  
  
3.  <span data-ttu-id="5dffb-132">Clique o **Add** botão da **associações de Site** caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="5dffb-132">Click the **Add** button of the **Site Bindings** dialog box.</span></span>  
  
4.  <span data-ttu-id="5dffb-133">Selecione **HTTPS** da **tipo** lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="5dffb-133">Select **HTTPS** from the **Type** drop-down list.</span></span>  
  
5.  <span data-ttu-id="5dffb-134">Selecione o **ServiceModelSamples-HTTPS-Server** da **certificado SSL** lista suspensa e clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="5dffb-134">Select the **ServiceModelSamples-HTTPS-Server** from the **SSL certificate** drop-down list and click **OK**.</span></span>  
  
6.  <span data-ttu-id="5dffb-135">Testar o acesso ao serviço em um navegador usando o endereço HTTPS `https://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="5dffb-135">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5dffb-136">Como o certificado de teste que você acabou de instalar não é um certificado confiável, você poderá encontrar avisos de segurança adicionais do Internet Explorer ao navegar em endereços Web locais protegidos por esse certificado.</span><span class="sxs-lookup"><span data-stu-id="5dffb-136">Because the test certificate you have just installed is not a trusted certificate, you may encounter additional Internet Explorer security warnings when browsing to local Web addresses secured with this certificate.</span></span>  
  
## <a name="removing-certificates"></a><span data-ttu-id="5dffb-137">Removendo certificados</span><span class="sxs-lookup"><span data-stu-id="5dffb-137">Removing Certificates</span></span>  
  
-   <span data-ttu-id="5dffb-138">Use o Gerenciador dos Serviços de Informações da Internet como direcionado anteriormente, mas remova o certificado ou associação em vez de adicionar.</span><span class="sxs-lookup"><span data-stu-id="5dffb-138">Use the Internet Information Services Manager as previously directed, but remove the certificate or binding instead of adding it.</span></span>  
  
-   <span data-ttu-id="5dffb-139">Remova o certificado do computador usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="5dffb-139">Remove the computer certificate by using the following command.</span></span>  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
