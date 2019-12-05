---
title: Utilizando as ferramentas de desenvolvimento do WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 59913f4c00c32699d788e2a0244798fc652361be
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802398"
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="35643-102">Utilizando as ferramentas de desenvolvimento do WCF</span><span class="sxs-lookup"><span data-stu-id="35643-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="35643-103">Esta seção descreve as ferramentas de desenvolvimento do Visual Studio que podem ajudá-lo a desenvolver seu WCFservice.</span><span class="sxs-lookup"><span data-stu-id="35643-103">This section describes the Visual Studio development tools that can assist you in developing your WCFservice.</span></span>  
  
 <span data-ttu-id="35643-104">Você pode usar os modelos do Visual Studio como uma base para criar rapidamente seu próprio serviço e, em seguida, usar o cliente de host automático do serviço WCF e de teste do WCF para depurar e testar seu serviço.</span><span class="sxs-lookup"><span data-stu-id="35643-104">You can use the Visual Studio templates as a foundation to quickly build your own service, then use WCF Service Auto Host and WCF Test Client to debug and test your service.</span></span> <span data-ttu-id="35643-105">Essas ferramentas juntas fornecem um ciclo de depuração e teste rápido e contínuo e impedem a necessidade de se comprometer com um modelo de hospedagem em um estágio inicial.</span><span class="sxs-lookup"><span data-stu-id="35643-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  
 
 > [!NOTE]
 > <span data-ttu-id="35643-106">A partir do Visual Studio 2017, as ferramentas de desenvolvimento do WCF não são instaladas por padrão.</span><span class="sxs-lookup"><span data-stu-id="35643-106">Starting with Visual Studio 2017, the WCF development tools are not installed by default.</span></span> <span data-ttu-id="35643-107">Para usar esses recursos, você deve garantir que o componente Windows Communication Foundation esteja selecionado no instalador do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="35643-107">In order to use these features, you must ensure the Windows Communication Foundation component is selected in the Visual Studio installer.</span></span>
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="35643-108">O WCF Ferramentas para Desenvolvedores</span><span class="sxs-lookup"><span data-stu-id="35643-108">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="35643-109">Modelos do Visual Studio do WCF</span><span class="sxs-lookup"><span data-stu-id="35643-109">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)  
  
 <span data-ttu-id="35643-110">Você pode usar os modelos de projeto e item predefinidos do Visual Studio no Visual Studio para criar rapidamente serviços WCF e aplicativos adjacentes.</span><span class="sxs-lookup"><span data-stu-id="35643-110">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="35643-111">Host de serviço do WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="35643-111">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="35643-112">O host automático do serviço WCF (WcfSvcHost. exe) permite que você inicie o depurador do Visual Studio (F5) para hospedar e testar automaticamente um serviço que você implementou.</span><span class="sxs-lookup"><span data-stu-id="35643-112">The WCF Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="35643-113">Em seguida, você pode testar o serviço usando o cliente de teste do WCF (wcfTestClient. exe) ou seu próprio cliente para localizar e corrigir quaisquer erros potenciais.</span><span class="sxs-lookup"><span data-stu-id="35643-113">You can then test the service using the WCF Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="35643-114">Cliente de teste do WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="35643-114">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)  
  
 <span data-ttu-id="35643-115">O cliente de teste do WCF (WcfTestClient. exe) é uma ferramenta de GUI que permite que você insira parâmetros de tipos arbitrários, envie essa entrada para o serviço e exiba a resposta que o serviço envia de volta.</span><span class="sxs-lookup"><span data-stu-id="35643-115">WCF Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="35643-116">Ele fornece uma experiência de teste de serviço sem interrupção quando combinado com o host automático do serviço WCF.</span><span class="sxs-lookup"><span data-stu-id="35643-116">It provides a seamless service testing experience when combined with WCF Service Auto Host.</span></span>  
  
 [<span data-ttu-id="35643-117">Gerando classes de tipo de dados por meio de XML</span><span class="sxs-lookup"><span data-stu-id="35643-117">Generating Data Type Classes from XML</span></span>](generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="35643-118">Os dados XML armazenados na área de transferência podem ser colados em uma página de código.</span><span class="sxs-lookup"><span data-stu-id="35643-118">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="35643-119">As classes definidas nos dados serão convertidas em tipos de código.</span><span class="sxs-lookup"><span data-stu-id="35643-119">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="35643-120">Usando o privilégio ferramentas sem administrador</span><span class="sxs-lookup"><span data-stu-id="35643-120">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="35643-121">Para permitir que os usuários sem privilégios de administrador desenvolvam serviços WCF, uma ACL (lista de controle de acesso) é criada para o namespace "http://+:8731/Design_Time_Addresses" durante a instalação do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="35643-121">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="35643-122">A ACL é definida como (UI), que inclui todos os usuários interativos conectados à máquina.</span><span class="sxs-lookup"><span data-stu-id="35643-122">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="35643-123">Os administradores podem adicionar ou remover usuários dessa ACL ou abrir portas adicionais. Essa ACL permite que os modelos WCF ou WF enviem e recebam dados em sua configuração padrão.</span><span class="sxs-lookup"><span data-stu-id="35643-123">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="35643-124">Ele também permite que os usuários usem o host automático do serviço WCF (wcfSvcHost. exe) sem conceder a eles privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="35643-124">It also enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="35643-125">Você pode modificar o acesso usando a ferramenta Netsh. exe no [!INCLUDE[wv](../../../includes/wv-md.md)] na conta de administrador elevada.</span><span class="sxs-lookup"><span data-stu-id="35643-125">You can modify access using the Netsh.exe tool in [!INCLUDE[wv](../../../includes/wv-md.md)] under the elevated administrator account.</span></span> <span data-ttu-id="35643-126">Veja a seguir um exemplo de como usar o netsh. exe.</span><span class="sxs-lookup"><span data-stu-id="35643-126">The following is an example of using Netsh.exe.</span></span>  
  
```console  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 <span data-ttu-id="35643-127">Para obter mais informações sobre o netsh. exe, consulte [como usar a ferramenta Netsh. exe e as opções de linha de comando](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10)).</span><span class="sxs-lookup"><span data-stu-id="35643-127">For more information about Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35643-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35643-128">See also</span></span>

- [<span data-ttu-id="35643-129">Modelos do Visual Studio do WCF</span><span class="sxs-lookup"><span data-stu-id="35643-129">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)
- [<span data-ttu-id="35643-130">Host de serviço do WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="35643-130">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
- [<span data-ttu-id="35643-131">Cliente de teste do WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="35643-131">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)
