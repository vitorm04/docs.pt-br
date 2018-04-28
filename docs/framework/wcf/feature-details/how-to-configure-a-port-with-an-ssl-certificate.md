---
title: Como configurar uma porta com um certificado SSL
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bbf3d4b9888d07a89d1b6a8225a7f7415e8c67cc
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="ede2e-102">Como configurar uma porta com um certificado SSL</span><span class="sxs-lookup"><span data-stu-id="ede2e-102">How to: Configure a Port with an SSL Certificate</span></span>
<span data-ttu-id="ede2e-103">Ao criar um serviço auto-hospedado do [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] com a classe <xref:System.ServiceModel.WSHttpBinding> que usa segurança de transporte, você também deve configurar uma porta com um certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="ede2e-103">When creating a self-hosted [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="ede2e-104">Se você estiver criando um serviço auto-hospedado, você poderá hospedá-lo serviço no IIS (Serviços de Informações da Internet).</span><span class="sxs-lookup"><span data-stu-id="ede2e-104">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="ede2e-105">Para obter mais informações, consulte [segurança de transporte HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="ede2e-105">For more information, see [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
 <span data-ttu-id="ede2e-106">Para configurar uma porta, a ferramenta usada depende do sistema operacional que está sendo executado no computador.</span><span class="sxs-lookup"><span data-stu-id="ede2e-106">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="ede2e-107">Se estiver executando o [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou o [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use a ferramenta HttpCfg.exe.</span><span class="sxs-lookup"><span data-stu-id="ede2e-107">If you are running [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool.</span></span> <span data-ttu-id="ede2e-108">Com o [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] essa ferramenta é instalada.</span><span class="sxs-lookup"><span data-stu-id="ede2e-108">With [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] this tool is installed.</span></span> <span data-ttu-id="ede2e-109">Com [!INCLUDE[wxp](../../../../includes/wxp-md.md)], você pode baixar a ferramenta em [ferramentas de suporte do Windows XP Service Pack 2](http://go.microsoft.com/fwlink/?LinkId=88606).</span><span class="sxs-lookup"><span data-stu-id="ede2e-109">With [!INCLUDE[wxp](../../../../includes/wxp-md.md)], you can download the tool at [Windows XP Service Pack 2 Support Tools](http://go.microsoft.com/fwlink/?LinkId=88606).</span></span> <span data-ttu-id="ede2e-110">Para obter mais informações, consulte [visão geral de Httpcfg](http://go.microsoft.com/fwlink/?LinkId=88605).</span><span class="sxs-lookup"><span data-stu-id="ede2e-110">For more information, see [Httpcfg Overview](http://go.microsoft.com/fwlink/?LinkId=88605).</span></span> <span data-ttu-id="ede2e-111">O [documentação de ferramentas de suporte do Windows](http://go.microsoft.com/fwlink/?LinkId=94840) explica a sintaxe para a ferramenta Httpcfg.exe.</span><span class="sxs-lookup"><span data-stu-id="ede2e-111">The [Windows Support Tools documentation](http://go.microsoft.com/fwlink/?LinkId=94840) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="ede2e-112">Se estiver executando o [!INCLUDE[wv](../../../../includes/wv-md.md)], use a ferramenta Netsh.exe que já está instalada.</span><span class="sxs-lookup"><span data-stu-id="ede2e-112">If you are running [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool that is already installed.</span></span>  
  
 <span data-ttu-id="ede2e-113">Este tópico descreve como executar vários procedimentos:</span><span class="sxs-lookup"><span data-stu-id="ede2e-113">This topic describes how to accomplish several procedures:</span></span>  
  
-   <span data-ttu-id="ede2e-114">Determinar a configuração atual da porta de um computador.</span><span class="sxs-lookup"><span data-stu-id="ede2e-114">Determining a computer's current port configuration.</span></span>  
  
-   <span data-ttu-id="ede2e-115">Obter impressão digital de um certificado (necessário para os próximos dois procedimentos).</span><span class="sxs-lookup"><span data-stu-id="ede2e-115">Getting a certificate's thumbprint (necessary for the following two procedures).</span></span>  
  
-   <span data-ttu-id="ede2e-116">Associar um certificado SSL a uma configuração de porta.</span><span class="sxs-lookup"><span data-stu-id="ede2e-116">Binding an SSL certificate to a port configuration.</span></span>  
  
-   <span data-ttu-id="ede2e-117">Associar um certificado SSL a uma configuração de porta e dar suporte a certificados do cliente.</span><span class="sxs-lookup"><span data-stu-id="ede2e-117">Binding an SSL certificate to a port configuration and supporting client certificates.</span></span>  
  
-   <span data-ttu-id="ede2e-118">Excluir um certificado SSL de um número de porta.</span><span class="sxs-lookup"><span data-stu-id="ede2e-118">Deleting an SSL certificate from a port number.</span></span>  
  
 <span data-ttu-id="ede2e-119">Observe que a modificação de certificados armazenados no computador requer privilégios administrativos.</span><span class="sxs-lookup"><span data-stu-id="ede2e-119">Note that modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
### <a name="to-determine-how-ports-are-configured"></a><span data-ttu-id="ede2e-120">Para determinar como as portas estão configuradas</span><span class="sxs-lookup"><span data-stu-id="ede2e-120">To determine how ports are configured</span></span>  
  
1.  <span data-ttu-id="ede2e-121">Em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use a ferramenta HttpCfg.exe para exibir a configuração da porta atual, usando o **consulta** e **ssl** comutadores, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ede2e-121">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```  
    httpcfg query ssl  
    ```  
  
2.  <span data-ttu-id="ede2e-122">No [!INCLUDE[wv](../../../../includes/wv-md.md)], use a ferramenta Netsh.exe para exibir a configuração atual da porta, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ede2e-122">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```  
    netsh http show sslcert  
    ```  
  
### <a name="to-get-a-certificates-thumbprint"></a><span data-ttu-id="ede2e-123">Para obter a impressão digital de um certificado</span><span class="sxs-lookup"><span data-stu-id="ede2e-123">To get a certificate's thumbprint</span></span>  
  
1.  <span data-ttu-id="ede2e-124">Use o snap-in do MMC dos Certificados para localizar um certificado X.509 cuja finalidade seja a autenticação de cliente.</span><span class="sxs-lookup"><span data-stu-id="ede2e-124">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="ede2e-125">Para obter mais informações, consulte [como: exibir certificados com o Snap-in do MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span><span class="sxs-lookup"><span data-stu-id="ede2e-125">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2.  <span data-ttu-id="ede2e-126">Para acessar a impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="ede2e-126">Access the certificate's thumbprint.</span></span> <span data-ttu-id="ede2e-127">Para obter mais informações, consulte [como: recuperar a impressão digital de um certificado](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span><span class="sxs-lookup"><span data-stu-id="ede2e-127">For more information, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3.  <span data-ttu-id="ede2e-128">Copie a impressão digital do certificado em um editor de texto, como o Bloco de Notas.</span><span class="sxs-lookup"><span data-stu-id="ede2e-128">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4.  <span data-ttu-id="ede2e-129">Remova todos os espaços entre os caracteres hexadecimais.</span><span class="sxs-lookup"><span data-stu-id="ede2e-129">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="ede2e-130">Uma maneira de fazer isso é usar o recurso localizar e substituir do editor de texto e substituir cada espaço com um caractere nulo.</span><span class="sxs-lookup"><span data-stu-id="ede2e-130">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="ede2e-131">Para associar um certificado SSL a um número de porta.</span><span class="sxs-lookup"><span data-stu-id="ede2e-131">To bind an SSL certificate to a port number</span></span>  
  
1.  <span data-ttu-id="ede2e-132">No [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou no [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use a ferramenta HttpCfg.exe no modo “set” no repositório SSL para associar o certificado a um número de porta.</span><span class="sxs-lookup"><span data-stu-id="ede2e-132">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="ede2e-133">A ferramenta usa a impressão digital para identificar o certificado, conforme mostrado no exemplo o seguir.</span><span class="sxs-lookup"><span data-stu-id="ede2e-133">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    -   <span data-ttu-id="ede2e-134">O **-i** switch tem a sintaxe de `IP`:`port` e instrui a ferramenta para definir o certificado à porta 8012 do computador.</span><span class="sxs-lookup"><span data-stu-id="ede2e-134">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="ede2e-135">Opcionalmente, os quatro zeros que precedem o número também podem ser substituídos pelo endereço IP real do computador.</span><span class="sxs-lookup"><span data-stu-id="ede2e-135">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    -   <span data-ttu-id="ede2e-136">O **-h** opção especifica a impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="ede2e-136">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2.  <span data-ttu-id="ede2e-137">No [!INCLUDE[wv](../../../../includes/wv-md.md)], use a ferramenta Netsh.exe, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ede2e-137">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}   
    ```  
  
    -   <span data-ttu-id="ede2e-138">O **certhash** parâmetro especifica a impressão digital do certificado.</span><span class="sxs-lookup"><span data-stu-id="ede2e-138">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    -   <span data-ttu-id="ede2e-139">O **ipport** parâmetro especifica o endereço IP e porta e funciona como o **-i** switch da ferramenta Httpcfg.exe descrita.</span><span class="sxs-lookup"><span data-stu-id="ede2e-139">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    -   <span data-ttu-id="ede2e-140">O **appid** parâmetro é um GUID que pode ser usado para identificar o aplicativo proprietário.</span><span class="sxs-lookup"><span data-stu-id="ede2e-140">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
### <a name="to-bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="ede2e-141">Para associar um certificado SSL a um número de porta e dar suporte a certificados do cliente</span><span class="sxs-lookup"><span data-stu-id="ede2e-141">To bind an SSL certificate to a port number and support client certificates</span></span>  
  
1.  <span data-ttu-id="ede2e-142">No [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou no [!INCLUDE[wxp](../../../../includes/wxp-md.md)], para dar suporte aos clientes que se autenticam com os certificados X.509 na camada de transporte, siga o procedimento anterior, mas inclua um parâmetro adicional de linha de comando em HttpCfg.exe, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ede2e-142">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="ede2e-143">O **-f** switch tem a sintaxe de `n` onde n é um número entre 1 e 7.</span><span class="sxs-lookup"><span data-stu-id="ede2e-143">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="ede2e-144">Um valor de 2, conforme mostrado no exemplo anterior, permite certificados do cliente na camada de transporte.</span><span class="sxs-lookup"><span data-stu-id="ede2e-144">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="ede2e-145">Um valor de 3 permite certificados do cliente e mapeia esses certificados para uma conta do Windows.</span><span class="sxs-lookup"><span data-stu-id="ede2e-145">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="ede2e-146">Consulte a Ajuda do HttpCfg.exe para obter o comportamento de outros valores.</span><span class="sxs-lookup"><span data-stu-id="ede2e-146">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2.  <span data-ttu-id="ede2e-147">No [!INCLUDE[wv](../../../../includes/wv-md.md)], para dar suporte aos clientes que se autenticam com os certificados X.509 na camada de transporte, siga o procedimento anterior, mas com um parâmetro adicional, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ede2e-147">In [!INCLUDE[wv](../../../../includes/wv-md.md)], to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
### <a name="to-delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="ede2e-148">Para excluir um certificado SSL de um número de porta</span><span class="sxs-lookup"><span data-stu-id="ede2e-148">To delete an SSL certificate from a port number</span></span>  
  
1.  <span data-ttu-id="ede2e-149">Use a ferramenta HttpCfg.exe ou Netsh.exe para ver as portas e as impressões digitais de todas as associações no computador.</span><span class="sxs-lookup"><span data-stu-id="ede2e-149">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="ede2e-150">Para imprimir informações em disco, use o caractere de redirecionamento ">", conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ede2e-150">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```  
    httpcfg query ssl>myMachinePorts.txt  
    ```  
  
2.  <span data-ttu-id="ede2e-151">Em [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] ou [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use a ferramenta HttpCfg.exe com o **excluir** e **ssl** palavras-chave.</span><span class="sxs-lookup"><span data-stu-id="ede2e-151">In [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] or [!INCLUDE[wxp](../../../../includes/wxp-md.md)], use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="ede2e-152">Use o **-i** para especificar o `IP`:`port` número e o **-h** para especificar a impressão digital.</span><span class="sxs-lookup"><span data-stu-id="ede2e-152">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3.  <span data-ttu-id="ede2e-153">No [!INCLUDE[wv](../../../../includes/wv-md.md)], use a ferramenta Netsh.exe, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ede2e-153">In [!INCLUDE[wv](../../../../includes/wv-md.md)], use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="ede2e-154">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ede2e-154">Example</span></span>  
 <span data-ttu-id="ede2e-155">O código a seguir mostra como criar um serviço auto-hospedado usando o conjunto de classes <xref:System.ServiceModel.WSHttpBinding> para segurança no transporte.</span><span class="sxs-lookup"><span data-stu-id="ede2e-155">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="ede2e-156">Ao criar um aplicativo, especifique o número da porta no endereço.</span><span class="sxs-lookup"><span data-stu-id="ede2e-156">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ede2e-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ede2e-157">See Also</span></span>  
 [<span data-ttu-id="ede2e-158">Segurança de transporte de HTTP</span><span class="sxs-lookup"><span data-stu-id="ede2e-158">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
