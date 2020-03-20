---
title: Utilizando as ferramentas de desenvolvimento do WCF
ms.date: 03/30/2017
ms.assetid: 054adb87-c244-4d5a-83d1-0b2b44bd454b
ms.openlocfilehash: 82bb7e225492bcdba4d2e611de405a09571355c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183075"
---
# <a name="using-the-wcf-development-tools"></a><span data-ttu-id="a554b-102">Utilizando as ferramentas de desenvolvimento do WCF</span><span class="sxs-lookup"><span data-stu-id="a554b-102">Using the WCF Development Tools</span></span>
<span data-ttu-id="a554b-103">Esta seção descreve as ferramentas de desenvolvimento do Visual Studio que podem ajudá-lo a desenvolver seu serviço WCFservice.</span><span class="sxs-lookup"><span data-stu-id="a554b-103">This section describes the Visual Studio development tools that can assist you in developing your WCFservice.</span></span>  
  
 <span data-ttu-id="a554b-104">Você pode usar os modelos do Visual Studio como base para construir rapidamente seu próprio serviço e, em seguida, usar o WCF Service Auto Host e o WCF Test Client para depurar e testar seu serviço.</span><span class="sxs-lookup"><span data-stu-id="a554b-104">You can use the Visual Studio templates as a foundation to quickly build your own service, then use WCF Service Auto Host and WCF Test Client to debug and test your service.</span></span> <span data-ttu-id="a554b-105">Essas ferramentas juntas fornecem um ciclo rápido e perfeito de depuração e teste, e impedem a necessidade de se comprometer com um modelo de hospedagem em um estágio inicial.</span><span class="sxs-lookup"><span data-stu-id="a554b-105">These tools together provide a fast and seamless debug and testing cycle, and preclude the need to commit to a hosting model at an early stage.</span></span>  

 > [!NOTE]
 > <span data-ttu-id="a554b-106">Começando pelo Visual Studio 2017, as ferramentas de desenvolvimento do WCF não são instaladas por padrão.</span><span class="sxs-lookup"><span data-stu-id="a554b-106">Starting with Visual Studio 2017, the WCF development tools are not installed by default.</span></span> <span data-ttu-id="a554b-107">Para usar esses recursos, você deve garantir que o componente da Windows Communication Foundation seja selecionado no instalador do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a554b-107">In order to use these features, you must ensure the Windows Communication Foundation component is selected in the Visual Studio installer.</span></span>
  
## <a name="the-wcf-developer-tools"></a><span data-ttu-id="a554b-108">As ferramentas de desenvolvedor do WCF</span><span class="sxs-lookup"><span data-stu-id="a554b-108">The WCF Developer Tools</span></span>  
 [<span data-ttu-id="a554b-109">Modelos do Visual Studio do WCF</span><span class="sxs-lookup"><span data-stu-id="a554b-109">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)  
  
 <span data-ttu-id="a554b-110">Você pode usar o projeto visual studio predefinido e modelos de itens no Visual Studio para criar rapidamente serviços WCF e aplicativos ao redor.</span><span class="sxs-lookup"><span data-stu-id="a554b-110">You can use the predefined Visual Studio project and item templates in Visual Studio to quickly build WCF services and surrounding applications.</span></span>  
  
 [<span data-ttu-id="a554b-111">Host de serviço do WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="a554b-111">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)  
  
 <span data-ttu-id="a554b-112">O WCF Service Auto Host (WcfSvcHost.exe) permite que você inicie o depurador visual studio (F5) para hospedar e testar automaticamente um serviço que você implementou.</span><span class="sxs-lookup"><span data-stu-id="a554b-112">The WCF Service Auto Host (WcfSvcHost.exe) allows you to launch the Visual Studio debugger (F5) to automatically host and test a service you have implemented.</span></span> <span data-ttu-id="a554b-113">Em seguida, você pode testar o serviço usando o WCF Test Client (wcfTestClient.exe) ou seu próprio cliente para encontrar e corrigir quaisquer possíveis erros.</span><span class="sxs-lookup"><span data-stu-id="a554b-113">You can then test the service using the WCF Test Client (wcfTestClient.exe) or your own client to find and fix any potential errors.</span></span>  
  
 [<span data-ttu-id="a554b-114">Cliente de Teste do WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="a554b-114">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)  
  
 <span data-ttu-id="a554b-115">WCF Test Client (WcfTestClient.exe) é uma ferramenta de GUI que permite inserir parâmetros de tipos arbitrários, enviar essa entrada para o serviço e visualizar a resposta que o serviço envia de volta.</span><span class="sxs-lookup"><span data-stu-id="a554b-115">WCF Test Client (WcfTestClient.exe) is a GUI tool that allows you to input parameters of arbitrary types, submit that input to the service, and view the response the service sends back.</span></span> <span data-ttu-id="a554b-116">Ele fornece uma experiência perfeita de teste de serviço quando combinado com o WCF Service Auto Host.</span><span class="sxs-lookup"><span data-stu-id="a554b-116">It provides a seamless service testing experience when combined with WCF Service Auto Host.</span></span>  
  
 [<span data-ttu-id="a554b-117">Gerando classes de tipo de dados por meio de XML</span><span class="sxs-lookup"><span data-stu-id="a554b-117">Generating Data Type Classes from XML</span></span>](generating-data-type-classes-from-xml.md)  
  
 <span data-ttu-id="a554b-118">Os dados XML armazenados na área de transferência podem ser colados em uma página de código.</span><span class="sxs-lookup"><span data-stu-id="a554b-118">XML data stored in the clipboard can be pasted into a code page.</span></span> <span data-ttu-id="a554b-119">As classes definidas nos dados serão convertidas em tipos de código.</span><span class="sxs-lookup"><span data-stu-id="a554b-119">The classes defined in the data will be converted to code types.</span></span>  
  
## <a name="using-the-tools-without-administrator-privilege"></a><span data-ttu-id="a554b-120">Usando as Ferramentas sem privilégio de administrador</span><span class="sxs-lookup"><span data-stu-id="a554b-120">Using the Tools without Administrator privilege</span></span>  
 <span data-ttu-id="a554b-121">Para permitir que os usuários sem privilégio de administrador desenvolvam serviços WCF,http://+:8731/Design_Time_Addressesuma ACL (Access Control List) é criada para o namespace " durante a instalação do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a554b-121">To enable users without administrator privilege to develop WCF services, an ACL (Access Control List) is created for the namespace "http://+:8731/Design_Time_Addresses" during the installation of Visual Studio.</span></span> <span data-ttu-id="a554b-122">A ACL é definida como (UI), que inclui todos os usuários interativos conectados à máquina.</span><span class="sxs-lookup"><span data-stu-id="a554b-122">The ACL is set to (UI), which includes all interactive users logged on to the machine.</span></span> <span data-ttu-id="a554b-123">Os administradores podem adicionar ou remover usuários desta ACL ou abrir portas adicionais. Esta ACL permite que os modelos WCF ou WF enviem e recebam dados em sua configuração padrão.</span><span class="sxs-lookup"><span data-stu-id="a554b-123">Administrators can add or remove users from this ACL, or open additional ports.This ACL enables WCF or WF templates to send and receive data in their default configuration.</span></span> <span data-ttu-id="a554b-124">Ele também permite que os usuários usem o WCF Service Auto Host (wcfSvcHost.exe) sem conceder privilégios de administrador.</span><span class="sxs-lookup"><span data-stu-id="a554b-124">It also enables users to use the WCF Service Auto Host (wcfSvcHost.exe) without granting them administrator privileges.</span></span>  
  
 <span data-ttu-id="a554b-125">Você pode modificar o acesso usando a ferramenta Netsh.exe no Windows Vista a conta de administrador elevada.</span><span class="sxs-lookup"><span data-stu-id="a554b-125">You can modify access using the Netsh.exe tool in Windows Vista under the elevated administrator account.</span></span> <span data-ttu-id="a554b-126">A seguir, um exemplo de uso do Netsh.exe.</span><span class="sxs-lookup"><span data-stu-id="a554b-126">The following is an example of using Netsh.exe.</span></span>  
  
```console  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 <span data-ttu-id="a554b-127">Para obter mais informações sobre o Netsh.exe, consulte [Como usar a ferramenta Netsh.exe e os switches de linha de comando](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10)).</span><span class="sxs-lookup"><span data-stu-id="a554b-127">For more information about Netsh.exe, see [How to Use the Netsh.exe Tool and Command-Line Switches](https://docs.microsoft.com/previous-versions/tn-archive/bb490939(v=technet.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a554b-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="a554b-128">See also</span></span>

- [<span data-ttu-id="a554b-129">Modelos do Visual Studio do WCF</span><span class="sxs-lookup"><span data-stu-id="a554b-129">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)
- [<span data-ttu-id="a554b-130">Host de serviço do WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="a554b-130">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
- [<span data-ttu-id="a554b-131">Cliente de Teste do WCF (WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="a554b-131">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)
