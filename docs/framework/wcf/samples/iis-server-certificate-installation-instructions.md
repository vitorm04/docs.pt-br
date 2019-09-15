---
title: Instruções da instalação do certificado de servidor dos Serviços de Informações da Internet (IIS)
ms.date: 03/30/2017
ms.assetid: 11281490-d2ac-4324-8f33-e7714611a34b
ms.openlocfilehash: 300d689925d60998ef475ad63f3878bf6d066850
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989849"
---
# <a name="internet-information-services-iis-server-certificate-installation-instructions"></a><span data-ttu-id="02d5e-102">Instruções da instalação do certificado de servidor dos Serviços de Informações da Internet (IIS)</span><span class="sxs-lookup"><span data-stu-id="02d5e-102">Internet Information Services (IIS) Server Certificate Installation Instructions</span></span>
<span data-ttu-id="02d5e-103">Para executar os exemplos que comunicam com segurança com o IIS (Serviços de Informações da Internet), você deverá criar e instalar um certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="02d5e-103">To run the samples that securely communicate with Internet Information Services (IIS), you must create and install a server certificate.</span></span>  
  
## <a name="step-1-creating-certificates"></a><span data-ttu-id="02d5e-104">Etapa 1.</span><span class="sxs-lookup"><span data-stu-id="02d5e-104">Step 1.</span></span> <span data-ttu-id="02d5e-105">Criando certificados</span><span class="sxs-lookup"><span data-stu-id="02d5e-105">Creating Certificates</span></span>  
 <span data-ttu-id="02d5e-106">Para criar um certificado para o computador, abra um Prompt de Comando do Desenvolvedor para o Visual Studio com privilégios de administrador e execute o setup. bat que está incluído em cada um dos exemplos que usam comunicação segura com o IIS.</span><span class="sxs-lookup"><span data-stu-id="02d5e-106">To create a certificate for your computer, open a Developer Command Prompt for Visual Studio with administrator privileges and run the Setup.bat that is included in each of the samples that use secure communication with IIS.</span></span> <span data-ttu-id="02d5e-107">Verifique se o caminho inclui a pasta que contém Makecert.exe antes de executar este arquivo em lote.</span><span class="sxs-lookup"><span data-stu-id="02d5e-107">Ensure that the path includes the folder that contains Makecert.exe before you run this batch file.</span></span> <span data-ttu-id="02d5e-108">O comando a seguir é usado para criar o certificado em Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="02d5e-108">The following command is used to create the certificate in Setup.bat.</span></span>  
  
```console  
makecert -sr LocalMachine -ss My -n CN=ServiceModelSamples-HTTPS-Server -sky exchange -sk ServiceModelSamples-HTTPS-Key  
```  
  
## <a name="step-2-installing-certificates"></a><span data-ttu-id="02d5e-109">Etapa 2.</span><span class="sxs-lookup"><span data-stu-id="02d5e-109">Step 2.</span></span> <span data-ttu-id="02d5e-110">Instalando certificados</span><span class="sxs-lookup"><span data-stu-id="02d5e-110">Installing Certificates</span></span>  
 <span data-ttu-id="02d5e-111">As etapas necessárias para instalar os certificados que você criou dependem de qual versão do IIS você está usando.</span><span class="sxs-lookup"><span data-stu-id="02d5e-111">The steps required to install the certificates you just created depend on which version of IIS you are using.</span></span>  
  
#### <a name="to-install-iis-on-iis-51-windows-xp-and-iis-60-windows-server-2003"></a><span data-ttu-id="02d5e-112">Para instalar o IIS no IIS 5.1 (Windows XP) e IIS 6.0 (Windows Server 2003)</span><span class="sxs-lookup"><span data-stu-id="02d5e-112">To install IIS on IIS 5.1 (Windows XP) and IIS 6.0 (Windows Server 2003)</span></span>  
  
1. <span data-ttu-id="02d5e-113">Abra o snap-in do MMC do Gerenciador dos Serviços de Informações da Internet.</span><span class="sxs-lookup"><span data-stu-id="02d5e-113">Open the Internet Information Services Manager MMC Snap-In.</span></span>  
  
2. <span data-ttu-id="02d5e-114">Clique com o botão direito do mouse no site da Web padrão e selecione **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="02d5e-114">Right-click the default Web site and select **Properties**.</span></span>  
  
3. <span data-ttu-id="02d5e-115">Selecione a guia **segurança de diretório** .</span><span class="sxs-lookup"><span data-stu-id="02d5e-115">Select the **Directory Security** tab.</span></span>  
  
4. <span data-ttu-id="02d5e-116">Clique no botão **certificado do servidor** .</span><span class="sxs-lookup"><span data-stu-id="02d5e-116">Click the **Server Certificate** button.</span></span> <span data-ttu-id="02d5e-117">O assistente de certificado do servidor Web é iniciado.</span><span class="sxs-lookup"><span data-stu-id="02d5e-117">The Web Server Certificate Wizard starts.</span></span>  
  
5. <span data-ttu-id="02d5e-118">Conclua o assistente.</span><span class="sxs-lookup"><span data-stu-id="02d5e-118">Complete the wizard.</span></span> <span data-ttu-id="02d5e-119">Selecione a opção para atribuir um certificado.</span><span class="sxs-lookup"><span data-stu-id="02d5e-119">Select the option to assign a certificate.</span></span> <span data-ttu-id="02d5e-120">Selecione o certificado ServiceModelSamples-HTTPS-Server da lista de certificados que são exibidos.</span><span class="sxs-lookup"><span data-stu-id="02d5e-120">Select the ServiceModelSamples-HTTPS-Server certificate from the list of certificates that are displayed.</span></span>  
  
     <span data-ttu-id="02d5e-121">![Assistente de certificado do IIS](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span><span class="sxs-lookup"><span data-stu-id="02d5e-121">![IIS Certificate Wizard](../../../../docs/framework/wcf/samples/media/iiscertificate-wizard.GIF "IISCertificate_Wizard")</span></span>  
  
6. <span data-ttu-id="02d5e-122">Teste o acesso ao serviço em um navegador usando o endereço `https://localhost/servicemodelsamples/service.svc`HTTPS.</span><span class="sxs-lookup"><span data-stu-id="02d5e-122">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
#### <a name="if-ssl-was-previously-configured-by-using-httpcfgexe"></a><span data-ttu-id="02d5e-123">Se o SSL foi configurado anteriormente usando Httpcfg.exe</span><span class="sxs-lookup"><span data-stu-id="02d5e-123">If SSL was previously configured by using Httpcfg.exe</span></span>  
  
1. <span data-ttu-id="02d5e-124">Use Makecert.exe (ou execute Setup.bat) para criar o certificado do servidor.</span><span class="sxs-lookup"><span data-stu-id="02d5e-124">Use Makecert.exe (or run Setup.bat) to create the server certificate.</span></span>  
  
2. <span data-ttu-id="02d5e-125">Execute o Gerenciador do IIS e instale o certificado de acordo com as etapas anteriores.</span><span class="sxs-lookup"><span data-stu-id="02d5e-125">Run the IIS manager and install the certificate according to the previous steps.</span></span>  
  
3. <span data-ttu-id="02d5e-126">Adicione a seguinte linha de código ao programa cliente.</span><span class="sxs-lookup"><span data-stu-id="02d5e-126">Add the following line of code to the client program.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="02d5e-127">Esse código somente é necessário para certificados de teste como os criados por Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="02d5e-127">This code is only required for test certificates such as those created by Makecert.exe.</span></span> <span data-ttu-id="02d5e-128">Não é recomendável para o código de produção.</span><span class="sxs-lookup"><span data-stu-id="02d5e-128">It is not recommended for production code.</span></span>  
  
```csharp  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
#### <a name="to-install-iis-on-iis-70-windows-vista-and-windows-server-2008"></a><span data-ttu-id="02d5e-129">Para instalar o IIS no IIS 7.0 (Windows Vista e Windows Server 2008)</span><span class="sxs-lookup"><span data-stu-id="02d5e-129">To install IIS on IIS 7.0 (Windows Vista and Windows Server 2008)</span></span>  
  
1. <span data-ttu-id="02d5e-130">No menu **Iniciar** , clique em **executar**e digite **inetmgr** para abrir o snap-in do MMC serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="02d5e-130">From the **Start** menu, click **Run**, then type **inetmgr** to open the Internet Information Services (IIS) MMC snap-in.</span></span>  
  
2. <span data-ttu-id="02d5e-131">Clique com o botão direito do mouse no **site da Web padrão** e selecione **Editar associações...**</span><span class="sxs-lookup"><span data-stu-id="02d5e-131">Right-click the **Default Web Site** and select **Edit Bindings…**</span></span>  
  
3. <span data-ttu-id="02d5e-132">Clique no botão **Adicionar** da caixa de diálogo **ligações do site** .</span><span class="sxs-lookup"><span data-stu-id="02d5e-132">Click the **Add** button of the **Site Bindings** dialog box.</span></span>  
  
4. <span data-ttu-id="02d5e-133">Selecione **https** na lista suspensa **tipo** .</span><span class="sxs-lookup"><span data-stu-id="02d5e-133">Select **HTTPS** from the **Type** drop-down list.</span></span>  
  
5. <span data-ttu-id="02d5e-134">Selecione o **ServiceModelSamples-https-Server** na lista suspensa **certificado SSL** e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="02d5e-134">Select the **ServiceModelSamples-HTTPS-Server** from the **SSL certificate** drop-down list and click **OK**.</span></span>  
  
6. <span data-ttu-id="02d5e-135">Teste o acesso ao serviço em um navegador usando o endereço `https://localhost/servicemodelsamples/service.svc`HTTPS.</span><span class="sxs-lookup"><span data-stu-id="02d5e-135">Test access to the service in a browser by using the HTTPS address `https://localhost/servicemodelsamples/service.svc`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02d5e-136">Como o certificado de teste que você acabou de instalar não é um certificado confiável, você poderá encontrar avisos de segurança adicionais do Internet Explorer ao navegar em endereços Web locais protegidos por esse certificado.</span><span class="sxs-lookup"><span data-stu-id="02d5e-136">Because the test certificate you have just installed is not a trusted certificate, you may encounter additional Internet Explorer security warnings when browsing to local Web addresses secured with this certificate.</span></span>  
  
## <a name="removing-certificates"></a><span data-ttu-id="02d5e-137">Removendo certificados</span><span class="sxs-lookup"><span data-stu-id="02d5e-137">Removing Certificates</span></span>  
  
- <span data-ttu-id="02d5e-138">Use o Gerenciador dos Serviços de Informações da Internet como direcionado anteriormente, mas remova o certificado ou associação em vez de adicionar.</span><span class="sxs-lookup"><span data-stu-id="02d5e-138">Use the Internet Information Services Manager as previously directed, but remove the certificate or binding instead of adding it.</span></span>  
  
- <span data-ttu-id="02d5e-139">Remova o certificado do computador usando o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="02d5e-139">Remove the computer certificate by using the following command.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:443  
    ```
