---
title: Ferramenta Configuration Editor (SvcConfigEditor.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
ms.openlocfilehash: 3d482e2b03346c9443066c480575a1394324b9bf
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320698"
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a><span data-ttu-id="09394-102">Ferramenta Configuration Editor (SvcConfigEditor.exe)</span><span class="sxs-lookup"><span data-stu-id="09394-102">Configuration Editor Tool (SvcConfigEditor.exe)</span></span>

<span data-ttu-id="09394-103">O editor de configuração de serviço do Windows Communication Foundation (WCF) (SvcConfigEditor. exe) permite que administradores e desenvolvedores criem e modifiquem definições de configuração para serviços WCF usando uma interface gráfica do usuário.</span><span class="sxs-lookup"><span data-stu-id="09394-103">The Windows Communication Foundation (WCF) Service Configuration Editor (SvcConfigEditor.exe) allows administrators and developers to create and modify configuration settings for WCF services using a graphical user interface.</span></span> <span data-ttu-id="09394-104">Com essa ferramenta, você pode gerenciar configurações para associações, comportamentos, serviços e diagnósticos do WCF sem precisar editar diretamente os arquivos de configuração XML.</span><span class="sxs-lookup"><span data-stu-id="09394-104">With this tool, you can manage settings for WCF bindings, behaviors, services, and diagnostics without having to directly edit XML configuration files.</span></span>

<span data-ttu-id="09394-105">O editor de configuração de serviço pode ser encontrado na pasta C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin</span><span class="sxs-lookup"><span data-stu-id="09394-105">Service Configuration Editor can be found in the C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin folder.</span></span>

## <a name="the-wcf-configuration-editor"></a><span data-ttu-id="09394-106">O editor de configuração do WCF</span><span class="sxs-lookup"><span data-stu-id="09394-106">The WCF Configuration Editor</span></span>

<span data-ttu-id="09394-107">O editor de configuração de serviço vem com um assistente que orienta você por todas as etapas de configuração de um serviço ou cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="09394-107">Service Configuration Editor comes with a wizard that guides you through all the steps in configuring a WCF service or client.</span></span> <span data-ttu-id="09394-108">É altamente recomendável usar o assistente em vez do editor diretamente.</span><span class="sxs-lookup"><span data-stu-id="09394-108">You are strongly advised to use the wizard instead of the editor directly.</span></span>

<span data-ttu-id="09394-109">Se você já tiver alguns arquivos de configuração que estão em conformidade com o esquema de sistema. configuração padrão, poderá gerenciar configurações específicas para associações, comportamento, serviços e diagnósticos com a interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="09394-109">If you already have some configuration files that comply with the standard System.Configuration schema, you can manage specific settings for bindings, behavior, services, and diagnostics with the user interface.</span></span> <span data-ttu-id="09394-110">O editor de configuração de serviço permite que você gerencie as configurações para arquivos de configuração do WCF existentes, bem como arquivos executáveis, serviços COM+ e serviços hospedados na Web.</span><span class="sxs-lookup"><span data-stu-id="09394-110">The Service Configuration Editor enables you to manage the settings for existing WCF configuration files as well as executable files, COM+ services, and Web-hosted services.</span></span> <span data-ttu-id="09394-111">Ao abrir um serviço hospedado na Web com o editor de configuração de serviço, as seções configuração do próprio serviço e configurações herdadas dos nós de nível superior são mostradas.</span><span class="sxs-lookup"><span data-stu-id="09394-111">When opening a Web-hosted service with Service Configuration Editor, both the service’s own configuration and inherited configurations sections of upper level nodes are shown.</span></span>

<span data-ttu-id="09394-112">Como as definições de configuração do WCF estão localizadas na seção `<system.serviceModel>` do arquivo de configuração, o editor opera exclusivamente no conteúdo desse elemento e não acessa outros elementos no mesmo arquivo.</span><span class="sxs-lookup"><span data-stu-id="09394-112">Because WCF configuration settings are located in the `<system.serviceModel>` section of the configuration file, the editor operates exclusively on the content of this element and does not access other elements in the same file.</span></span> <span data-ttu-id="09394-113">Você pode navegar diretamente para os arquivos de configuração existentes ou pode selecionar um assembly que contenha um serviço, um diretório virtual ou um serviço COM+.</span><span class="sxs-lookup"><span data-stu-id="09394-113">You can navigate to existing configuration files directly or you can select an assembly that contains a service, virtual directory, or COM+ service.</span></span> <span data-ttu-id="09394-114">O editor carrega o arquivo de configuração para esse serviço específico e permite que o usuário adicione novos elementos ou edite elementos existentes aninhados na seção `<system.serviceModel>` do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="09394-114">The editor loads the configuration file for that particular service and allows the user to either add new elements or edit existing elements nested in the `<system.serviceModel>` section of the configuration file.</span></span>

<span data-ttu-id="09394-115">O editor dá suporte ao IntelliSense e impõe a conformidade do esquema.</span><span class="sxs-lookup"><span data-stu-id="09394-115">The editor supports IntelliSense and enforces schema compliance.</span></span> <span data-ttu-id="09394-116">A saída resultante é garantida para estar em conformidade com o esquema do arquivo de configuração e para ter valores de dados sintaticamente corretos.</span><span class="sxs-lookup"><span data-stu-id="09394-116">The resulting output is guaranteed to comply with the schema of the configuration file and to have syntactically correct data values.</span></span> <span data-ttu-id="09394-117">No entanto, o editor não garante que o arquivo de configuração seja semanticamente válido.</span><span class="sxs-lookup"><span data-stu-id="09394-117">However, the editor does not guarantee that the configuration file is semantically valid.</span></span> <span data-ttu-id="09394-118">Em outras palavras, o editor não garante que o arquivo de configuração possa funcionar com o serviço que ele configura.</span><span class="sxs-lookup"><span data-stu-id="09394-118">In other words, the editor does not guarantee that the configuration file can work with the service it configures.</span></span>

> [!CAUTION]
> <span data-ttu-id="09394-119">O editor não pode limpar um elemento de configuração do arquivo de configuração depois que você modificou o elemento.</span><span class="sxs-lookup"><span data-stu-id="09394-119">The editor cannot purge a configuration element from the configuration file once you have modified the element.</span></span> <span data-ttu-id="09394-120">Por exemplo, se você usar o editor para definir o nome do ponto de extremidade como uma cadeia de caracteres não vazia e salvá-lo, o arquivo de configuração terá o seguinte conteúdo, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="09394-120">For example, if you use the editor to set the endpoint name to a non-empty string and save it, the configuration file has the following content, as shown in the following example.</span></span>
>
> `<endpoint binding="basicHttpBinding" name="somename" />`
>
> <span data-ttu-id="09394-121">Se você tentar remover o nome definindo-o como uma cadeia de caracteres vazia e salvar o arquivo, o arquivo de configuração ainda conterá o atributo `name`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="09394-121">If you attempt to remove the name by setting it to an empty string and save the file, the configuration file still contains the `name` attribute, as shown in the following example.</span></span>
>
> `<endpoint binding="basicHttpBinding" name="" />`
>
> <span data-ttu-id="09394-122">Para limpar o atributo, você deve editar manualmente o elemento usando outro editor de texto.</span><span class="sxs-lookup"><span data-stu-id="09394-122">To purge the attribute, you must manually edit the element using another text editor.</span></span>
>
> <span data-ttu-id="09394-123">Você deve ser especialmente cuidadoso com esse problema ao usar o elemento `issueToken` do comportamento de ponto de extremidade `clientCredential`.</span><span class="sxs-lookup"><span data-stu-id="09394-123">You should be especially careful with this issue when you use the `issueToken` element of the `clientCredential` Endpoint behavior.</span></span> <span data-ttu-id="09394-124">Especificamente, o atributo `address` de seu subelemento `localIssuer` não deve ser uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="09394-124">Specifically, the `address` attribute of its `localIssuer` sub-element must not be an empty string.</span></span> <span data-ttu-id="09394-125">Se você tiver modificado o atributo `address` usando o editor de configuração e quiser removê-lo completamente, deverá fazer isso usando uma ferramenta diferente do editor.</span><span class="sxs-lookup"><span data-stu-id="09394-125">If you have modified the `address` attribute using the Configuration Editor and want to remove it completely, you should do so using a tool other than the Editor.</span></span> <span data-ttu-id="09394-126">Caso contrário, o atributo contém uma cadeia de caracteres vazia e seu aplicativo gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="09394-126">Otherwise, the attribute contains an empty string and your application throws an exception.</span></span>

## <a name="using-the-configuration-editor"></a><span data-ttu-id="09394-127">Usando o editor de configuração</span><span class="sxs-lookup"><span data-stu-id="09394-127">Using the Configuration Editor</span></span>

<span data-ttu-id="09394-128">O editor de configuração de serviço pode ser encontrado no seguinte local de instalação do SDK do Windows:</span><span class="sxs-lookup"><span data-stu-id="09394-128">The Service Configuration Editor can be found at the following Windows SDK installation location:</span></span>

<span data-ttu-id="09394-129">C:\Arquivos de Programas\microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe</span><span class="sxs-lookup"><span data-stu-id="09394-129">C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe</span></span>

<span data-ttu-id="09394-130">Depois de iniciar o editor de configuração de serviço, você pode usar o menu **arquivo/abrir** para procurar o serviço ou o assembly que deseja gerenciar.</span><span class="sxs-lookup"><span data-stu-id="09394-130">After you launch the Service Configuration Editor, you can use the **File/Open** menu to browse for the service or assembly you want to manage.</span></span> <span data-ttu-id="09394-131">Você pode abrir os arquivos de configuração diretamente, procurar serviços WCF/COM + e abrir arquivos de configuração para serviços hospedados na Web.</span><span class="sxs-lookup"><span data-stu-id="09394-131">You can open configuration files directly, browse for WCF /COM+ services, and open configuration files for Web-hosted services.</span></span>

<span data-ttu-id="09394-132">A interface do usuário do editor de configuração de serviço é dividida nas seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="09394-132">The Service Configuration Editor's user interface is divided into the following areas:</span></span>

- <span data-ttu-id="09394-133">Painel exibição de árvore, que exibe elementos de configuração em uma estrutura de árvore à esquerda.</span><span class="sxs-lookup"><span data-stu-id="09394-133">Tree View Pane, which displays configuration elements in a tree structure on the left.</span></span> <span data-ttu-id="09394-134">Você pode executar operações na árvore clicando com o botão direito do mouse nos nós.</span><span class="sxs-lookup"><span data-stu-id="09394-134">You can perform operations in the tree by right-clicking the nodes.</span></span>

- <span data-ttu-id="09394-135">Painel de tarefas, que exibe tarefas comuns para os elementos atuais no canto inferior esquerdo da janela</span><span class="sxs-lookup"><span data-stu-id="09394-135">Task Pane, which displays common tasks for current elements on the lower-left of the window</span></span>

- <span data-ttu-id="09394-136">Painel de detalhes, que exibe as configurações detalhadas do nó de configuração selecionado no modo de exibição de árvore à direita.</span><span class="sxs-lookup"><span data-stu-id="09394-136">Detail Pane, which displays detailed settings of the configuration node selected in the Tree View on the right.</span></span>

### <a name="opening-a-configuration-file"></a><span data-ttu-id="09394-137">Abrindo um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="09394-137">Opening a Configuration File</span></span>

1. <span data-ttu-id="09394-138">Inicie o editor de configuração de serviço usando uma janela de comando para navegar até o local de instalação do WCF e digite `SvcConfigEditor.exe`.</span><span class="sxs-lookup"><span data-stu-id="09394-138">Start Service Configuration Editor by using a command window to navigate to your WCF installation location, and then type `SvcConfigEditor.exe`.</span></span>

2. <span data-ttu-id="09394-139">No menu **arquivo** , selecione **abrir** e clique no tipo de arquivo que você deseja gerenciar.</span><span class="sxs-lookup"><span data-stu-id="09394-139">From the **File** menu, select **Open** and click the type of file you want to manage.</span></span>

3. <span data-ttu-id="09394-140">Na caixa de diálogo **abrir** , navegue até o arquivo específico que você deseja gerenciar e clique duas vezes nele.</span><span class="sxs-lookup"><span data-stu-id="09394-140">In the **Open** dialog box, navigate to the specific file you want to manage and double-click it.</span></span>

<span data-ttu-id="09394-141">O visualizador segue automaticamente o caminho de mesclagem de configuração e cria uma exibição da configuração mesclada.</span><span class="sxs-lookup"><span data-stu-id="09394-141">The viewer automatically follows the configuration merge path and creates a view of the merged configuration.</span></span> <span data-ttu-id="09394-142">Por exemplo, a configuração real de um serviço não hospedado é uma combinação de Machine. config e app. config. Todas as alterações são aplicadas ao arquivo ativo no SvcConfigEditor.</span><span class="sxs-lookup"><span data-stu-id="09394-142">For example, the actual configuration of a non-hosted service is a combination of Machine.config and App.config. Any changes are applied to the active file in the SvcConfigEditor.</span></span> <span data-ttu-id="09394-143">Se você quiser editar um arquivo específico no caminho de mesclagem de configuração, deverá abri-lo diretamente.</span><span class="sxs-lookup"><span data-stu-id="09394-143">If you want to edit a specific file in the configuration merge path, you should open it directly.</span></span>

> [!NOTE]
> <span data-ttu-id="09394-144">O editor de configuração recarrega o arquivo de configuração aberto no momento quando o último é modificado fora do editor.</span><span class="sxs-lookup"><span data-stu-id="09394-144">Configuration Editor reloads the currently opened configuration file when the latter has been modified outside the Editor.</span></span> <span data-ttu-id="09394-145">Quando isso acontece, todas as alterações que não são permanentemente salvas dentro do editor são perdidas.</span><span class="sxs-lookup"><span data-stu-id="09394-145">When this happens, all the changes that are not durably saved inside the Editor are lost.</span></span> <span data-ttu-id="09394-146">Se o recarregamento ocorrer consistentemente, a causa mais provável é um serviço que acessa constantemente o arquivo de configuração, por exemplo, um software antivírus em execução em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="09394-146">If reloading happens consistently, the most likely cause is a service that constantly accesses the configuration file, for example, an antivirus software running in the background.</span></span> <span data-ttu-id="09394-147">Para resolver isso, verifique se o editor de configuração é o único processo que pode acessar o arquivo quando ele é aberto.</span><span class="sxs-lookup"><span data-stu-id="09394-147">To resolve this, ensure that Configuration Editor is the only process that can access the file when it is opened.</span></span>

### <a name="services"></a><span data-ttu-id="09394-148">Serviços</span><span class="sxs-lookup"><span data-stu-id="09394-148">Services</span></span>

<span data-ttu-id="09394-149">O nó **Serviços** exibe todos os serviços atualmente atribuídos no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="09394-149">The **Services** node displays all of the services currently assigned in the configuration file.</span></span> <span data-ttu-id="09394-150">Cada subnó na árvore corresponde a um subelemento do < `services` > elemento no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="09394-150">Each sub-node in the tree corresponds to a sub-element of the <`services`> element in the configuration file.</span></span>

<span data-ttu-id="09394-151">Ao clicar no nó **Serviços** , você pode exibir ou executar tarefas na página Resumo do serviço no painel de **detalhes** .</span><span class="sxs-lookup"><span data-stu-id="09394-151">When you click the **Services** node, you can view or perform tasks on the service Summary Page in the **Detail** Pane.</span></span>

#### <a name="creating-a-new-service-configuration"></a><span data-ttu-id="09394-152">Criando uma nova configuração de serviço</span><span class="sxs-lookup"><span data-stu-id="09394-152">Creating a new Service Configuration</span></span>

<span data-ttu-id="09394-153">Você pode criar uma nova configuração de serviço das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="09394-153">You can create a new service configuration in the following ways:</span></span>

- <span data-ttu-id="09394-154">Usando um assistente: clique no link **criar um novo serviço...**</span><span class="sxs-lookup"><span data-stu-id="09394-154">Using a Wizard: Click the link **Create a New Service…**</span></span> <span data-ttu-id="09394-155">no painel de tarefas ou na página Resumo para iniciar o assistente.</span><span class="sxs-lookup"><span data-stu-id="09394-155">on the Task Pane or Summary Page to launch the wizard.</span></span> <span data-ttu-id="09394-156">Você também pode fazer isso no menu **arquivo** -> **Adicionar novo item**.</span><span class="sxs-lookup"><span data-stu-id="09394-156">You can also do so in the **File** menu -> **Add New Item**.</span></span>

- <span data-ttu-id="09394-157">Criar manualmente: você pode clicar com o botão direito do mouse no nó **Serviços** e escolher **novo serviço**.</span><span class="sxs-lookup"><span data-stu-id="09394-157">Create manually: You can right-click the **Services** node and choose **New Service**.</span></span>

#### <a name="creating-a-new-service-endpoint-configuration"></a><span data-ttu-id="09394-158">Criando uma nova configuração de ponto de extremidade de serviço</span><span class="sxs-lookup"><span data-stu-id="09394-158">Creating a new Service Endpoint Configuration</span></span>

<span data-ttu-id="09394-159">Você pode criar uma nova configuração de ponto de extremidade de serviço das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="09394-159">You can create a new service endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="09394-160">Criar usando um assistente: clique no link **criar um novo ponto de extremidade de serviço...**</span><span class="sxs-lookup"><span data-stu-id="09394-160">Create using a Wizard: click the link **Create a New Service Endpoint…**</span></span> <span data-ttu-id="09394-161">no painel de tarefas ou na página Resumo para iniciar o assistente.</span><span class="sxs-lookup"><span data-stu-id="09394-161">on the Task Pane or Summary Page to launch the wizard.</span></span> <span data-ttu-id="09394-162">Você também pode fazer isso no menu **arquivo** -> **Adicionar novo item**.</span><span class="sxs-lookup"><span data-stu-id="09394-162">You can also do so in the **File** menu -> **Add New Item**.</span></span>

- <span data-ttu-id="09394-163">Criar manualmente: depois de criar um serviço, clique com o botão direito do mouse no nó **pontos** de extremidade e escolha "**novo ponto de extremidade de serviço**".</span><span class="sxs-lookup"><span data-stu-id="09394-163">Create manually: Once you created a Service, you can right-click the **Endpoints** node and choose "**New Service Endpoint**".</span></span>

#### <a name="editing-a-service-configuration"></a><span data-ttu-id="09394-164">Editando uma configuração de serviço</span><span class="sxs-lookup"><span data-stu-id="09394-164">Editing a Service Configuration</span></span>

1. <span data-ttu-id="09394-165">Clique em um nó de **serviço** .</span><span class="sxs-lookup"><span data-stu-id="09394-165">Click a **Service** node.</span></span>

2. <span data-ttu-id="09394-166">Edite as configurações nas grades de propriedade.</span><span class="sxs-lookup"><span data-stu-id="09394-166">Edit the settings in the property grids.</span></span>

#### <a name="editing-a-service-endpoint-configuration"></a><span data-ttu-id="09394-167">Editando uma configuração de ponto de extremidade de serviço</span><span class="sxs-lookup"><span data-stu-id="09394-167">Editing a Service Endpoint Configuration</span></span>

1. <span data-ttu-id="09394-168">Clique em um nó de **ponto de extremidade de serviço** .</span><span class="sxs-lookup"><span data-stu-id="09394-168">Click a **Service Endpoint** node.</span></span>

2. <span data-ttu-id="09394-169">Edite as configurações nas grades de propriedade.</span><span class="sxs-lookup"><span data-stu-id="09394-169">Edit the settings in the property grids.</span></span>

#### <a name="adding-a-base-address"></a><span data-ttu-id="09394-170">Adicionando um endereço base</span><span class="sxs-lookup"><span data-stu-id="09394-170">Adding a Base Address</span></span>

1. <span data-ttu-id="09394-171">Clique no nó **host** .</span><span class="sxs-lookup"><span data-stu-id="09394-171">Click the **Host** node.</span></span>

2. <span data-ttu-id="09394-172">Clique no botão **novo...**</span><span class="sxs-lookup"><span data-stu-id="09394-172">Click the **New…**</span></span> <span data-ttu-id="09394-173">na seção **endereços base** .</span><span class="sxs-lookup"><span data-stu-id="09394-173">button in the **Base Addresses** section.</span></span>

3. <span data-ttu-id="09394-174">Digite o URI do endereço base na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="09394-174">Type in the base address URI in the dialog box.</span></span>

4. <span data-ttu-id="09394-175">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="09394-175">Click **OK**.</span></span>

> [!NOTE]
> <span data-ttu-id="09394-176">Não é possível editar o valor de [\<baseAddressPrefixFilters >](../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) dentro dessa ferramenta.</span><span class="sxs-lookup"><span data-stu-id="09394-176">You cannot edit the value of [\<baseAddressPrefixFilters>](../configure-apps/file-schema/wcf/baseaddressprefixfilters.md) inside this tool.</span></span> <span data-ttu-id="09394-177">Para adicionar ou modificar esse elemento, você deve usar um editor de texto ou o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="09394-177">To add or modify this element, you should use a text editor or Visual Studio.</span></span>

### <a name="client"></a><span data-ttu-id="09394-178">Cliente</span><span class="sxs-lookup"><span data-stu-id="09394-178">Client</span></span>

<span data-ttu-id="09394-179">O nó **cliente** exibe todos os pontos de extremidade do cliente no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="09394-179">The **Client** node displays all of the client endpoints in the configuration file.</span></span> <span data-ttu-id="09394-180">Cada subnó na árvore corresponde a um subelemento do < `client` > elemento no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="09394-180">Every sub-node in the tree corresponds to a sub-element of the <`client`> element in the configuration file.</span></span>

<span data-ttu-id="09394-181">Ao clicar no nó **cliente** , você pode exibir ou executar tarefas na **página Resumo** do cliente no painel de **detalhes**.</span><span class="sxs-lookup"><span data-stu-id="09394-181">When you click the **Client** node, you can view or perform tasks on the client **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-client-endpoint-configuration"></a><span data-ttu-id="09394-182">Criando uma nova configuração de ponto de extremidade de cliente</span><span class="sxs-lookup"><span data-stu-id="09394-182">Creating a new Client Endpoint Configuration</span></span>

<span data-ttu-id="09394-183">Você pode criar uma nova configuração de ponto de extremidade de cliente das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="09394-183">You can create a new client endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="09394-184">Criar por assistente: clique no link **criar um novo cliente...**</span><span class="sxs-lookup"><span data-stu-id="09394-184">Create by Wizard: Click the link **Create a New Client…**</span></span> <span data-ttu-id="09394-185">no **painel de tarefas** na parte inferior esquerda da janela ou **página Resumo** para iniciar o assistente.</span><span class="sxs-lookup"><span data-stu-id="09394-185">on the **Task Pane** on the lower-left of the window, or **Summary Page** to launch the wizard.</span></span> <span data-ttu-id="09394-186">Você também pode fazer isso no menu **arquivo** -> **Adicionar novo item**.</span><span class="sxs-lookup"><span data-stu-id="09394-186">You can also do so in the **File** menu -> **Add New Item**.</span></span> <span data-ttu-id="09394-187">O assistente solicita que você aponte para o local da configuração do serviço, do qual a configuração do cliente é gerada.</span><span class="sxs-lookup"><span data-stu-id="09394-187">The wizard prompts you to point to the location of the service configuration, from which the client configuration is generated.</span></span> <span data-ttu-id="09394-188">Você pode escolher o ponto de extremidade de serviço ao qual se conectar.</span><span class="sxs-lookup"><span data-stu-id="09394-188">You can then choose the service endpoint to connect to.</span></span>

- <span data-ttu-id="09394-189">Criar manualmente: clique com o botão direito do mouse no nó **pontos de extremidade** em **cliente**e escolha **novo ponto de extremidade do cliente**.</span><span class="sxs-lookup"><span data-stu-id="09394-189">Create manually: Right-click the **Endpoints** node under **Client**, and choose **New Client Endpoint**.</span></span>

#### <a name="editing-a-client-endpoint-configuration"></a><span data-ttu-id="09394-190">Editando uma configuração de ponto de extremidade do cliente</span><span class="sxs-lookup"><span data-stu-id="09394-190">Editing a Client Endpoint Configuration</span></span>

1. <span data-ttu-id="09394-191">Clique em um nó de **ponto de extremidade do cliente** .</span><span class="sxs-lookup"><span data-stu-id="09394-191">Click a **Client Endpoint** node.</span></span>

2. <span data-ttu-id="09394-192">Edite as configurações nas grades de propriedade.</span><span class="sxs-lookup"><span data-stu-id="09394-192">Edit the settings in the property grids.</span></span>

### <a name="standard-endpoint"></a><span data-ttu-id="09394-193">Ponto de extremidade padrão</span><span class="sxs-lookup"><span data-stu-id="09394-193">Standard Endpoint</span></span>

<span data-ttu-id="09394-194">Os pontos de extremidade padrão são pontos de extremidade especializados que têm um ou mais aspectos do endereço, contrato e Associação definidos para valores padrão.</span><span class="sxs-lookup"><span data-stu-id="09394-194">Standard endpoints are specialized endpoints that have one or more aspects of the address, contract and binding set to default values.</span></span>

<span data-ttu-id="09394-195">Essas definições de configuração são armazenadas no nó do **ponto de extremidade padrão** .</span><span class="sxs-lookup"><span data-stu-id="09394-195">Such configuration settings are stored in the **Standard Endpoint** node.</span></span> <span data-ttu-id="09394-196">O nó do **ponto de extremidade padrão** exibe todas as configurações do ponto de extremidade padrão no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="09394-196">The **Standard Endpoint** node displays all of the standard endpoint settings in the configuration file.</span></span> <span data-ttu-id="09394-197">Cada subnó na árvore corresponde a um subelemento no elemento `<standardEndpoints>` no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="09394-197">Every sub-node in the tree corresponds to a sub-element in the `<standardEndpoints>` element in the configuration file.</span></span>

<span data-ttu-id="09394-198">Ao clicar no nó do **ponto de extremidade padrão** , você pode exibir ou executar tarefas na **página Resumo** do ponto de extremidade padrão no painel de **detalhes**.</span><span class="sxs-lookup"><span data-stu-id="09394-198">When you click the **Standard Endpoint** node, you can view or perform tasks on the standard endpoint **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-standard-endpoint-configuration"></a><span data-ttu-id="09394-199">Criando uma nova configuração de ponto de extremidade padrão</span><span class="sxs-lookup"><span data-stu-id="09394-199">Creating a New Standard Endpoint Configuration</span></span>

<span data-ttu-id="09394-200">Você pode criar uma nova configuração de ponto de extremidade padrão das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="09394-200">You can create a new standard endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="09394-201">Clique com o botão direito do mouse no nó do **ponto de extremidade padrão** e selecione **nova configuração de ponto de extremidade padrão...**</span><span class="sxs-lookup"><span data-stu-id="09394-201">Right-click the **Standard Endpoint** node and select **New Standard Endpoint Configuration…**</span></span> <span data-ttu-id="09394-202">Selecione o tipo de associação na caixa de diálogo e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="09394-202">Select the binding type in the dialog box and click **OK**.</span></span>

- <span data-ttu-id="09394-203">Selecione o nó do **ponto de extremidade padrão** e clique em **nova configuração de ponto de extremidade padrão...**</span><span class="sxs-lookup"><span data-stu-id="09394-203">Select the **Standard Endpoint** node and click **New Standard Endpoint Configuration…**</span></span> <span data-ttu-id="09394-204">no **painel de tarefas** na parte inferior esquerda da janela.</span><span class="sxs-lookup"><span data-stu-id="09394-204">in the **Task Pane** on the lower-left of the window.</span></span>

<span data-ttu-id="09394-205">A caixa de diálogo **criando um novo ponto de extremidade padrão** exibe e lista todos os tipos de ponto de extremidade padrão registrados.</span><span class="sxs-lookup"><span data-stu-id="09394-205">The **Creating a New Standard Endpoint** dialog box displays and lists all registered standard endpoint types.</span></span>

#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a><span data-ttu-id="09394-206">Exibindo e editando uma configuração de ponto de extremidade padrão</span><span class="sxs-lookup"><span data-stu-id="09394-206">Viewing and Editing a Standard Endpoint Configuration</span></span>

<span data-ttu-id="09394-207">Você pode abrir uma configuração de ponto de extremidade padrão para exibição e edição das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="09394-207">You can open a standard endpoint configuration for viewing and editing in the following ways:</span></span>

- <span data-ttu-id="09394-208">Clique para expandir o nó de **ponto de extremidade padrão** e clique no respectivo subnó de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="09394-208">Click to expand the **Standard Endpoint** node and click the respective endpoint sub-node.</span></span>

- <span data-ttu-id="09394-209">Clique no nó **ponto de extremidade padrão** e clique no respectivo ponto de extremidade no painel de detalhes.</span><span class="sxs-lookup"><span data-stu-id="09394-209">Click the **Standard Endpoint** node and click the respective endpoint on the Detail pane.</span></span>

<span data-ttu-id="09394-210">Os atributos para o ponto de extremidade são mostrados no painel direito para edição.</span><span class="sxs-lookup"><span data-stu-id="09394-210">Attributes for the endpoint are shown in the right pane for editing.</span></span>

#### <a name="deleting-a-standard-endpoint-configuration"></a><span data-ttu-id="09394-211">Excluindo uma configuração de ponto de extremidade padrão</span><span class="sxs-lookup"><span data-stu-id="09394-211">Deleting a Standard Endpoint Configuration</span></span>

<span data-ttu-id="09394-212">Você pode excluir uma configuração de ponto de extremidade padrão das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="09394-212">You can delete a standard endpoint configuration in the following ways:</span></span>

- <span data-ttu-id="09394-213">Clique para expandir o nó do **ponto de extremidade padrão** e clique com o botão direito do mouse no respectivo subnó de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="09394-213">Click to expand the **Standard Endpoint** node and right-click the respective endpoint sub-node.</span></span> <span data-ttu-id="09394-214">Use o comando de contexto **Excluir configuração de ponto de extremidade padrão** para excluir o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="09394-214">Use the context command **Delete Standard Endpoint Configuration** to delete the endpoint.</span></span>

- <span data-ttu-id="09394-215">Clique no nó do **ponto de extremidade padrão** .</span><span class="sxs-lookup"><span data-stu-id="09394-215">Click the **Standard Endpoint** node.</span></span> <span data-ttu-id="09394-216">No painel de **tarefas** , clique em **Excluir configuração de ponto de extremidade padrão**.</span><span class="sxs-lookup"><span data-stu-id="09394-216">In the **Task** pane, click **Delete Standard Endpoint Configuration**.</span></span>

<span data-ttu-id="09394-217">Se o ponto de extremidade padrão estiver em uso, uma mensagem de aviso será exibida quando você tentar excluí-lo: **o ponto de extremidade padrão está em uso. Se você excluí-lo agora, certifique-se de excluir todas as suas referências em outras partes da configuração (por exemplo, no ponto de extremidade de serviço ou ponto de extremidade do cliente). Caso contrário, a configuração será inválida e não poderá ser aberta da próxima vez. Tem certeza de que deseja excluir o ponto de extremidade padrão? "**</span><span class="sxs-lookup"><span data-stu-id="09394-217">If the standard endpoint is in used, a warning message is displayed when you attempt to delete it: **The standard endpoint is in use. If you delete it now, please be sure to delete all of its references in other parts of the configuration (for example, in the service endpoint or client endpoint). Otherwise, the configuration will be invalid and cannot be opened next time. Are you sure you want to delete the standard endpoint?"**</span></span>

### <a name="binding"></a><span data-ttu-id="09394-218">Associação</span><span class="sxs-lookup"><span data-stu-id="09394-218">Binding</span></span>

<span data-ttu-id="09394-219">As configurações de associação são usadas para configurar associações em pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="09394-219">Binding configurations are used to configure bindings on endpoints.</span></span> <span data-ttu-id="09394-220">Essas definições de configuração são armazenadas no nó de **Associação** .</span><span class="sxs-lookup"><span data-stu-id="09394-220">Such configuration settings are stored in the **Binding** node.</span></span> <span data-ttu-id="09394-221">Os pontos de extremidade fazem referência a configurações de associação por nome e vários pontos de extremidade podem fazer referência a uma única configuração de associação.</span><span class="sxs-lookup"><span data-stu-id="09394-221">Endpoints reference binding configurations by name and multiple endpoints can reference a single binding configuration.</span></span>

<span data-ttu-id="09394-222">O nó **associações** exibe todas as configurações de associação no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="09394-222">The **Bindings** node displays all of the binding settings in the configuration file.</span></span> <span data-ttu-id="09394-223">Cada subnó na árvore corresponde a um subelemento no elemento < `bindings` > no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="09394-223">Every sub-node in the tree corresponds to a sub-element in the <`bindings`> element in the configuration file.</span></span>

<span data-ttu-id="09394-224">Ao clicar no nó **associações** , você pode exibir ou executar tarefas na **página Resumo** da associação no **painel de detalhes**.</span><span class="sxs-lookup"><span data-stu-id="09394-224">When you click the **Bindings** node, you can view or perform tasks on the binding **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="creating-a-new-binding-configuration"></a><span data-ttu-id="09394-225">Criando uma nova configuração de associação</span><span class="sxs-lookup"><span data-stu-id="09394-225">Creating a New Binding Configuration</span></span>

<span data-ttu-id="09394-226">Você pode criar uma nova configuração de Associação das seguintes maneiras.</span><span class="sxs-lookup"><span data-stu-id="09394-226">You can create a new binding configuration in the following ways.</span></span>

- <span data-ttu-id="09394-227">Clique com o botão direito do mouse no nó **associações** e selecione **nova configuração de associação**...</span><span class="sxs-lookup"><span data-stu-id="09394-227">Right-click the **Bindings** node and select **New Binding Configuration**…</span></span> <span data-ttu-id="09394-228">Selecione o tipo de associação na caixa de diálogo e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="09394-228">Select the binding type in the dialog box and click **OK**.</span></span>

- <span data-ttu-id="09394-229">Selecione o nó **associações** e clique em **nova configuração de associação**...</span><span class="sxs-lookup"><span data-stu-id="09394-229">Select the **Bindings** node and click **New Binding Configuration**…</span></span> <span data-ttu-id="09394-230">no **painel de tarefas** na parte inferior esquerda da janela.</span><span class="sxs-lookup"><span data-stu-id="09394-230">in the **Task Pane** on the lower-left of the window.</span></span>

- <span data-ttu-id="09394-231">Na página Resumo do serviço ou do cliente, clique **em clique para criar** no campo **configuração de associação** para criar uma configuração de associação para o ponto de extremidade correspondente.</span><span class="sxs-lookup"><span data-stu-id="09394-231">In the service or client summary page, click **Click to Create** in the **Binding Configuration** field to create a binding configuration for the corresponding endpoint.</span></span>

#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a><span data-ttu-id="09394-232">Adicionando extensões de elemento de associação a uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="09394-232">Adding Binding Element Extensions to a Custom Binding</span></span>

1. <span data-ttu-id="09394-233">Selecione a associação à qual você deseja adicionar um elemento de extensão.</span><span class="sxs-lookup"><span data-stu-id="09394-233">Select the binding you want to add an extension element to.</span></span>

2. <span data-ttu-id="09394-234">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="09394-234">Click **Add**.</span></span>

3. <span data-ttu-id="09394-235">Na lista de extensões disponíveis, selecione a extensão de elemento de associação que você deseja adicionar.</span><span class="sxs-lookup"><span data-stu-id="09394-235">From the list of available extensions, select the binding element extension you want to add.</span></span> <span data-ttu-id="09394-236">Para selecionar vários itens, pressione a tecla CTRL simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="09394-236">To select multiple items, press the CTRL key simultaneously.</span></span>

4. <span data-ttu-id="09394-237">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="09394-237">Click **Add**.</span></span>

#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a><span data-ttu-id="09394-238">Ajustando a posição da extensão em uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="09394-238">Adjusting the Extension Position in a Custom Binding</span></span>

<span data-ttu-id="09394-239">Uma associação personalizada é uma coleção de elementos de associação que formam uma pilha.</span><span class="sxs-lookup"><span data-stu-id="09394-239">A custom binding is a collection of binding elements that form a stack.</span></span> <span data-ttu-id="09394-240">Cada elemento de ligação na pilha tem suas próprias definições de configuração.</span><span class="sxs-lookup"><span data-stu-id="09394-240">Each binding element on the stack has its own configuration settings.</span></span> <span data-ttu-id="09394-241">A ordem das extensões de elemento de associação em uma associação personalizada indica suas posições na pilha.</span><span class="sxs-lookup"><span data-stu-id="09394-241">The order of the binding element extensions in a custom binding indicates their positions in the stack.</span></span> <span data-ttu-id="09394-242">Os elementos na parte superior da pilha são aplicados primeiro.</span><span class="sxs-lookup"><span data-stu-id="09394-242">Elements at the top of the stack are applied first.</span></span> <span data-ttu-id="09394-243">Para alterar a ordem:</span><span class="sxs-lookup"><span data-stu-id="09394-243">To change the ordering:</span></span>

1. <span data-ttu-id="09394-244">Selecione o nó de associação personalizado.</span><span class="sxs-lookup"><span data-stu-id="09394-244">Select the custom binding node.</span></span>

2. <span data-ttu-id="09394-245">Selecione um elemento de extensão de associação na seção **posição da extensão do elemento de associação** .</span><span class="sxs-lookup"><span data-stu-id="09394-245">Select one binding extension element in the **Binding Element Extension Position** section.</span></span>

3. <span data-ttu-id="09394-246">Use o botão para **cima** ou **para baixo** no lado esquerdo da lista para alterar a posição do elemento selecionado.</span><span class="sxs-lookup"><span data-stu-id="09394-246">Use the **Up** or **Down** button on the left side of the list to change the position of the selected element.</span></span>

#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a><span data-ttu-id="09394-247">Editando a configuração de extensões de elemento de associação em uma associação personalizada</span><span class="sxs-lookup"><span data-stu-id="09394-247">Editing the Configuration of Binding Element Extensions in a Custom Binding</span></span>

1. <span data-ttu-id="09394-248">Selecione o nó de associação na árvore.</span><span class="sxs-lookup"><span data-stu-id="09394-248">Select the binding node in the tree.</span></span>

2. <span data-ttu-id="09394-249">Selecione a associação personalizada que contém o elemento que você deseja editar.</span><span class="sxs-lookup"><span data-stu-id="09394-249">Select the custom binding that contains the element you want to edit.</span></span>

3. <span data-ttu-id="09394-250">Selecione a extensão de elemento de associação que você deseja editar.</span><span class="sxs-lookup"><span data-stu-id="09394-250">Select the binding element extension you want to edit.</span></span> <span data-ttu-id="09394-251">As configurações do elemento aparecem no painel direito, onde podem ser editadas.</span><span class="sxs-lookup"><span data-stu-id="09394-251">The settings of the element appear in the right pane, where they can be edited.</span></span>

### <a name="diagnostics"></a><span data-ttu-id="09394-252">Diagnóstico</span><span class="sxs-lookup"><span data-stu-id="09394-252">Diagnostics</span></span>

<span data-ttu-id="09394-253">O nó **diagnóstico** exibe todas as configurações de diagnóstico no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="09394-253">The **Diagnostics** node displays all of the diagnostic settings in the configuration file.</span></span> <span data-ttu-id="09394-254">Ele permite ativar ou desativar os contadores de desempenho, habilitar ou desabilitar Instrumentação de Gerenciamento do Windows (WMI), configurar o rastreamento do WCF e configurar o log de mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="09394-254">It enables you to turn performance counters on or off, enable or disable Windows Management Instrumentation (WMI), configure WCF tracing, and configure WCF message logging.</span></span> <span data-ttu-id="09394-255">As configurações no nó **diagnóstico** correspondem à seção < `system.diagnostics` > e à seção `<diagnostics>` no `<system.serviceModel>` no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="09394-255">The settings in the **Diagnostics** node correspond to the <`system.diagnostics`> section, and `<diagnostics>` section in `<system.serviceModel>` in the configuration file.</span></span>

<span data-ttu-id="09394-256">Ao clicar no nó **diagnóstico** , você pode exibir ou executar tarefas na **página Resumo** do diagnóstico no painel de **detalhes**.</span><span class="sxs-lookup"><span data-stu-id="09394-256">When you click the **Diagnostics** node, you can view or perform tasks on the diagnostics **Summary Page** in the **Detail Pane**.</span></span>

#### <a name="configuring-performance-counters-and-wmi"></a><span data-ttu-id="09394-257">Configurando contadores de desempenho e WMI</span><span class="sxs-lookup"><span data-stu-id="09394-257">Configuring performance counters and WMI</span></span>

1. <span data-ttu-id="09394-258">Clique no nó **diagnóstico** .</span><span class="sxs-lookup"><span data-stu-id="09394-258">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="09394-259">Clique em **alternar contadores de desempenho**.</span><span class="sxs-lookup"><span data-stu-id="09394-259">Click **Toggle Performance Counters**.</span></span> <span data-ttu-id="09394-260">O contador de desempenho tem três Estados: desativado (padrão), somente de um e de todos.</span><span class="sxs-lookup"><span data-stu-id="09394-260">The performance counter has three states: Off (default), ServiceOnly, and All.</span></span> <span data-ttu-id="09394-261">Clicar no link alterna a configuração entre esses três Estados.</span><span class="sxs-lookup"><span data-stu-id="09394-261">Clicking the link toggles the setting among these three states.</span></span>

#### <a name="configuring-wmi-provider"></a><span data-ttu-id="09394-262">Configurando o provedor WMI</span><span class="sxs-lookup"><span data-stu-id="09394-262">Configuring WMI Provider</span></span>

1. <span data-ttu-id="09394-263">Clique no nó **diagnóstico** .</span><span class="sxs-lookup"><span data-stu-id="09394-263">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="09394-264">Para habilitar o provedor WMI, clique no link **habilitar provedor WMI** .</span><span class="sxs-lookup"><span data-stu-id="09394-264">To enable WMI provider, click the **Enable WMI Provider** link.</span></span>

#### <a name="enabling-wcf-tracing"></a><span data-ttu-id="09394-265">Habilitando o rastreamento do WCF</span><span class="sxs-lookup"><span data-stu-id="09394-265">Enabling WCF Tracing</span></span>

<span data-ttu-id="09394-266">Você pode criar um arquivo de rastreamento do WCF com propriedades padrão ou configurar um arquivo de rastreamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="09394-266">You can create a WCF trace file with standard properties or set up a custom trace file.</span></span>

1. <span data-ttu-id="09394-267">Clique no nó **diagnóstico** .</span><span class="sxs-lookup"><span data-stu-id="09394-267">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="09394-268">Clique em **Habilitar rastreamento**.</span><span class="sxs-lookup"><span data-stu-id="09394-268">Click **Enable Tracing**.</span></span>

3. <span data-ttu-id="09394-269">Clique no link **nível de rastreamento** para ajustar o nível de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="09394-269">Click the **Trace Level** link to adjust the trace level.</span></span> <span data-ttu-id="09394-270">Há seis níveis de rastreamento: desativado, crítico, erro, aviso, informações e detalhado.</span><span class="sxs-lookup"><span data-stu-id="09394-270">There are six trace levels: Off, Critical, Error, Warning, Information, and Verbose.</span></span> <span data-ttu-id="09394-271">A opção **rastreamento** de atividade e **propagar atividade** permite que você use o recurso de rastreamento de atividade do WCF.</span><span class="sxs-lookup"><span data-stu-id="09394-271">The **Activity Tracing** and **Propagate Activity** option enable you to use the WCF activity tracing feature.</span></span>

4. <span data-ttu-id="09394-272">Clique no nome do ouvinte de rastreamento para especificar o arquivo de rastreamento e as opções.</span><span class="sxs-lookup"><span data-stu-id="09394-272">Click the trace listener name to specify the trace file and options.</span></span>

#### <a name="enabling-wcf-logging"></a><span data-ttu-id="09394-273">Habilitando o log do WCF</span><span class="sxs-lookup"><span data-stu-id="09394-273">Enabling WCF Logging</span></span>

<span data-ttu-id="09394-274">Você pode criar um arquivo de rastreamento do WCF com propriedades padrão ou configurar um arquivo de rastreamento personalizado.</span><span class="sxs-lookup"><span data-stu-id="09394-274">You can create a WCF trace file with standard properties or set up a custom trace file.</span></span>

1. <span data-ttu-id="09394-275">Clique no nó **diagnóstico** .</span><span class="sxs-lookup"><span data-stu-id="09394-275">Click the **Diagnostics** node.</span></span>

2. <span data-ttu-id="09394-276">Clique em **habilitar log de mensagens**.</span><span class="sxs-lookup"><span data-stu-id="09394-276">Click **Enable Message Logging**.</span></span>

3. <span data-ttu-id="09394-277">Clique no link **nível de log** para ajustar o nível de log.</span><span class="sxs-lookup"><span data-stu-id="09394-277">Click the **Log Level** link to adjust the log level.</span></span> <span data-ttu-id="09394-278">Há três níveis de log: malformados, de serviço e de transporte.</span><span class="sxs-lookup"><span data-stu-id="09394-278">There are three log levels: Malformed, Service, and Transport.</span></span>

4. <span data-ttu-id="09394-279">Clique no nome do ouvinte para especificar o arquivo de log e as opções.</span><span class="sxs-lookup"><span data-stu-id="09394-279">Click the listener name to specify the log file and options.</span></span>

> [!NOTE]
> <span data-ttu-id="09394-280">Se você quiser que os logs de rastreamento e de mensagem sejam liberados automaticamente quando seu aplicativo for fechado, habilite a opção de **liberação automática** .</span><span class="sxs-lookup"><span data-stu-id="09394-280">If you want the trace and message logs to be flushed automatically when your application is closed, enable the **Auto Flush** option.</span></span>

<span data-ttu-id="09394-281">A **página Resumo** do diagnóstico permite que você realize as tarefas mais comuns na configuração de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="09394-281">The **Diagnostics** **Summary Page** enables you to accomplish the most common tasks in configuring diagnostics.</span></span> <span data-ttu-id="09394-282">No entanto, se você quiser editar manualmente as configurações de ouvintes e fontes, será necessário expandir o nó **diagnóstico** e editar as configurações em **log de mensagens**, **ouvintes** e nó de **fontes** .</span><span class="sxs-lookup"><span data-stu-id="09394-282">However, if you want to manually edit the Listeners and Sources settings, you must expand the **Diagnostics** node and edit settings in **Message Logging**, **Listeners** and **Sources** node.</span></span>

#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a><span data-ttu-id="09394-283">Habilitando o rastreamento personalizado do WCF ou o log de mensagens</span><span class="sxs-lookup"><span data-stu-id="09394-283">Enabling WCF Custom Tracing or Message Logging</span></span>

1. <span data-ttu-id="09394-284">Clique no nó **diagnóstico** e expanda-o.</span><span class="sxs-lookup"><span data-stu-id="09394-284">Click the **Diagnostics** node, and expand it.</span></span>

2. <span data-ttu-id="09394-285">Clique com o botão direito do mouse no nó **ouvintes** e selecione **novo ouvinte**.</span><span class="sxs-lookup"><span data-stu-id="09394-285">Right-click the **Listeners** node and select **New Listener**.</span></span>

3. <span data-ttu-id="09394-286">Digite o nome do arquivo de rastreamento no campo **initdata** .</span><span class="sxs-lookup"><span data-stu-id="09394-286">Type in the trace file name in the **InitData** field.</span></span> <span data-ttu-id="09394-287">Você pode clicar no botão "..." botão para navegar até um caminho.</span><span class="sxs-lookup"><span data-stu-id="09394-287">You can click the "…" button to browse to a path.</span></span>

4. <span data-ttu-id="09394-288">Clicar na linha **TypeName** exibe um "..." Button.</span><span class="sxs-lookup"><span data-stu-id="09394-288">Clicking the **TypeName** line displays a "…" button.</span></span> <span data-ttu-id="09394-289">Clique neste botão para abrir o **navegador do tipo de ouvinte de rastreamento**, que você pode usar para localizar ouvintes de rastreamento pré-configurados que já estão instalados.</span><span class="sxs-lookup"><span data-stu-id="09394-289">Click this button to open the **Trace Listener Type Browser**, which you can use to find pre-configured trace listeners that are already installed.</span></span>

5. <span data-ttu-id="09394-290">Observe a seção **origem** .</span><span class="sxs-lookup"><span data-stu-id="09394-290">Note the **Source** section.</span></span> <span data-ttu-id="09394-291">Clique em **Adicionar** nesta seção para abrir uma caixa de diálogo com um menu suspenso, que lista as fontes de rastreamento disponíveis.</span><span class="sxs-lookup"><span data-stu-id="09394-291">Click **Add** in this section to open a dialog box with a drop-down menu, which lists available tracing sources.</span></span> <span data-ttu-id="09394-292">Selecione uma origem de rastreamento e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="09394-292">Select a tracing source and click **OK**.</span></span>

6. <span data-ttu-id="09394-293">Para editar as configurações de log de mensagens, clique no nó **log de mensagens** .</span><span class="sxs-lookup"><span data-stu-id="09394-293">To edit Message Logging settings, click the **Message Logging** node.</span></span> <span data-ttu-id="09394-294">Você pode editar as configurações na grade de propriedades.</span><span class="sxs-lookup"><span data-stu-id="09394-294">You can edit the settings in the property grid.</span></span>

### <a name="advanced"></a><span data-ttu-id="09394-295">Avançado</span><span class="sxs-lookup"><span data-stu-id="09394-295">Advanced</span></span>

#### <a name="behaviors"></a><span data-ttu-id="09394-296">Comportamentos</span><span class="sxs-lookup"><span data-stu-id="09394-296">Behaviors</span></span>

<span data-ttu-id="09394-297">O nó **comportamentos** exibe os comportamentos atualmente definidos no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="09394-297">The **Behaviors** node displays the behaviors that are currently defined in the configuration file.</span></span>

<span data-ttu-id="09394-298">As configurações de comportamento são usadas para configurar comportamentos de pontos de extremidade e serviços.</span><span class="sxs-lookup"><span data-stu-id="09394-298">Behavior configurations are used to configure behaviors of endpoints and services.</span></span> <span data-ttu-id="09394-299">Essas definições de configuração são armazenadas no nó **avançado** em comportamentos de **serviço** e comportamentos de **ponto de extremidade**.</span><span class="sxs-lookup"><span data-stu-id="09394-299">Such configuration settings are stored in the **Advanced** node under **Service Behaviors** and **Endpoint Behaviors**.</span></span> <span data-ttu-id="09394-300">Os comportamentos de serviço são usados pelos serviços; enquanto os comportamentos de ponto de extremidade por pontos de extremidades.</span><span class="sxs-lookup"><span data-stu-id="09394-300">Service behaviors are used by services; whereas endpoint behaviors by endpoints.</span></span>

<span data-ttu-id="09394-301">Os comportamentos são uma coleção de elementos de extensão que para uma pilha.</span><span class="sxs-lookup"><span data-stu-id="09394-301">Behaviors are a collection of extension elements that for a stack.</span></span> <span data-ttu-id="09394-302">O elemento na parte superior da pilha é aplicado primeiro.</span><span class="sxs-lookup"><span data-stu-id="09394-302">The element at the top of the stack is applied first.</span></span> <span data-ttu-id="09394-303">Cada elemento de extensão pode ter sua própria configuração.</span><span class="sxs-lookup"><span data-stu-id="09394-303">Each extension element can have its own configuration.</span></span>

##### <a name="creating-a-new-behavior-configuration"></a><span data-ttu-id="09394-304">Criando uma nova configuração de comportamento</span><span class="sxs-lookup"><span data-stu-id="09394-304">Creating a new Behavior Configuration</span></span>

<span data-ttu-id="09394-305">Você pode criar uma nova configuração de comportamento de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="09394-305">You can create a new behavior configuration in two ways.</span></span>

- <span data-ttu-id="09394-306">Clique com o botão direito do mouse em um dos nós de comportamento e selecione "**nova configuração de comportamento...**</span><span class="sxs-lookup"><span data-stu-id="09394-306">Right-click one of the behavior nodes and select "**New Behavior Configuration…**</span></span>

- <span data-ttu-id="09394-307">Selecione um dos nós de comportamento e clique na **nova configuração de comportamento**...</span><span class="sxs-lookup"><span data-stu-id="09394-307">Select one of the behavior nodes and click the **New Behavior Configuration**…</span></span> <span data-ttu-id="09394-308">no **painel de tarefas** na parte inferior esquerda da janela.</span><span class="sxs-lookup"><span data-stu-id="09394-308">in the **Task Pane** on the lower-left of the window.</span></span>

##### <a name="adding-behavior-element-extensions-to-a-behavior"></a><span data-ttu-id="09394-309">Adicionando extensões de elemento de comportamento a um comportamento</span><span class="sxs-lookup"><span data-stu-id="09394-309">Adding Behavior Element Extensions to a Behavior</span></span>

1. <span data-ttu-id="09394-310">Selecione um dos nós de comportamento.</span><span class="sxs-lookup"><span data-stu-id="09394-310">Select one of the behavior nodes.</span></span>

2. <span data-ttu-id="09394-311">Selecione o comportamento que você deseja editar.</span><span class="sxs-lookup"><span data-stu-id="09394-311">Select the behavior you want edit.</span></span>

3. <span data-ttu-id="09394-312">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="09394-312">Click **Add**.</span></span>

4. <span data-ttu-id="09394-313">Na lista de extensões disponíveis, selecione a extensão de elemento de comportamento que você deseja adicionar.</span><span class="sxs-lookup"><span data-stu-id="09394-313">From the list of available extensions, select the behavior element extension you want to add.</span></span>

5. <span data-ttu-id="09394-314">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="09394-314">Click **Add**.</span></span>

##### <a name="adjusting-the-extension-position-in-a-behavior"></a><span data-ttu-id="09394-315">Ajustando a posição da extensão em um comportamento</span><span class="sxs-lookup"><span data-stu-id="09394-315">Adjusting the Extension Position in a Behavior</span></span>

<span data-ttu-id="09394-316">Os comportamentos são coleções de elementos que formam uma pilha.</span><span class="sxs-lookup"><span data-stu-id="09394-316">Behaviors are collections of elements that form a stack.</span></span> <span data-ttu-id="09394-317">Cada elemento na pilha tem sua própria configuração.</span><span class="sxs-lookup"><span data-stu-id="09394-317">Each element on the stack has its own configuration.</span></span> <span data-ttu-id="09394-318">A ordem das extensões de elemento de comportamento em um comportamento indica suas posições na pilha.</span><span class="sxs-lookup"><span data-stu-id="09394-318">The order of the behavior element extensions in a behavior indicates their positions in the stack.</span></span> <span data-ttu-id="09394-319">Os elementos na parte superior da pilha são aplicados primeiro.</span><span class="sxs-lookup"><span data-stu-id="09394-319">Elements at the top of the stack are applied first.</span></span> <span data-ttu-id="09394-320">Para alterar a ordem:</span><span class="sxs-lookup"><span data-stu-id="09394-320">To change the ordering:</span></span>

1. <span data-ttu-id="09394-321">Selecione um dos nós de comportamento.</span><span class="sxs-lookup"><span data-stu-id="09394-321">Select one of the behavior nodes.</span></span>

2. <span data-ttu-id="09394-322">Selecione o comportamento que você deseja editar.</span><span class="sxs-lookup"><span data-stu-id="09394-322">Select the behavior you want edit.</span></span>

3. <span data-ttu-id="09394-323">Selecione um elemento de extensão de comportamento na seção **posição de extensão do elemento de comportamento** .</span><span class="sxs-lookup"><span data-stu-id="09394-323">Select a behavior extension element in the **Behavior Element Extension Position** section.</span></span>

4. <span data-ttu-id="09394-324">Use o botão para **cima** ou **para baixo** no lado esquerdo da lista para alterar a posição do elemento selecionado.</span><span class="sxs-lookup"><span data-stu-id="09394-324">Use the **Up** or **Down** button on the left side of the list to change the position of the selected element.</span></span>

##### <a name="editing-the-configuration-of-behavior-element-extensions"></a><span data-ttu-id="09394-325">Editando a configuração das extensões de elemento de comportamento</span><span class="sxs-lookup"><span data-stu-id="09394-325">Editing the Configuration of Behavior Element Extensions</span></span>

1. <span data-ttu-id="09394-326">Selecione um dos nós de comportamento na árvore.</span><span class="sxs-lookup"><span data-stu-id="09394-326">Select one of the behavior nodes in the tree.</span></span>

2. <span data-ttu-id="09394-327">Selecione o comportamento que contém o elemento que você deseja editar.</span><span class="sxs-lookup"><span data-stu-id="09394-327">Select the behavior that contains the element you want to edit.</span></span>

3. <span data-ttu-id="09394-328">Selecione a extensão de elemento de comportamento que você deseja editar.</span><span class="sxs-lookup"><span data-stu-id="09394-328">Select the behavior element extension you want to edit.</span></span> <span data-ttu-id="09394-329">As configurações do elemento aparecem no painel direito, onde podem ser editadas.</span><span class="sxs-lookup"><span data-stu-id="09394-329">The settings of the element appear in the right pane where they can be edited.</span></span>

#### <a name="protocolmapping"></a><span data-ttu-id="09394-330">ProtocolMapping</span><span class="sxs-lookup"><span data-stu-id="09394-330">ProtocolMapping</span></span>

<span data-ttu-id="09394-331">Esta seção permite que você defina tipos de associação padrão para protocolos diferentes, como http, TCP, MSMQ ou net. pipe por meio de mapeamento definido entre esquemas de endereço de protocolo e as associações possíveis.</span><span class="sxs-lookup"><span data-stu-id="09394-331">This section allows you to set default binding types for different protocols such as http, tcp, MSMQ or net.pipe through defined mapping between protocol address schemes and the possible bindings.</span></span> <span data-ttu-id="09394-332">Você também pode adicionar novos mapeamentos a outros protocolos.</span><span class="sxs-lookup"><span data-stu-id="09394-332">You can also add new mappings to other protocols.</span></span>

#### <a name="extensions"></a><span data-ttu-id="09394-333">Extensões</span><span class="sxs-lookup"><span data-stu-id="09394-333">Extensions</span></span>

<span data-ttu-id="09394-334">Novas extensões de associação, extensões de elemento de associação, extensões de ponto de extremidade padrão e extensões de comportamento podem ser registradas para uso na configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="09394-334">New binding extensions, binding element extensions, standard endpoint extensions and behavior extensions can be registered for use in WCF configuration.</span></span> <span data-ttu-id="09394-335">As extensões são pares de nome/tipo.</span><span class="sxs-lookup"><span data-stu-id="09394-335">Extensions are name/type pairs.</span></span> <span data-ttu-id="09394-336">O nome define o nome da extensão na configuração, enquanto o tipo implementa a extensão.</span><span class="sxs-lookup"><span data-stu-id="09394-336">The name defines the name of the extension in configuration, whereas the type implements the extension.</span></span> <span data-ttu-id="09394-337">Há quatro tipos de extensões:</span><span class="sxs-lookup"><span data-stu-id="09394-337">There are four types of extensions:</span></span>

- <span data-ttu-id="09394-338">As extensões de associação definem um tipo de associação inteiro.</span><span class="sxs-lookup"><span data-stu-id="09394-338">Binding extensions define an entire binding type.</span></span> <span data-ttu-id="09394-339">Exemplo: `basicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="09394-339">Example: `basicHttpBinding`.</span></span>

- <span data-ttu-id="09394-340">As extensões de elemento de associação definem um elemento de uma associação.</span><span class="sxs-lookup"><span data-stu-id="09394-340">Binding element extensions define an element of a binding.</span></span> <span data-ttu-id="09394-341">Exemplo: `textMessageEncoding`.</span><span class="sxs-lookup"><span data-stu-id="09394-341">Example: `textMessageEncoding`.</span></span>

- <span data-ttu-id="09394-342">As extensões de ponto de extremidade padrão definem um ponto de extremidade padrão inteiro.</span><span class="sxs-lookup"><span data-stu-id="09394-342">Standard endpoint extensions define an entire standard endpoint.</span></span> <span data-ttu-id="09394-343">Exemplo: `discoveryEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="09394-343">Example: `discoveryEndpoint`.</span></span>

- <span data-ttu-id="09394-344">As extensões de elemento de comportamento definem um elemento de um comportamento.</span><span class="sxs-lookup"><span data-stu-id="09394-344">Behavior element extensions define an element of a behavior.</span></span> <span data-ttu-id="09394-345">Exemplo: `clientVia`.</span><span class="sxs-lookup"><span data-stu-id="09394-345">Example: `clientVia`.</span></span>

 <span data-ttu-id="09394-346">As extensões que foram registradas na configuração podem ser usadas como qualquer outro componente WCF do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="09394-346">Extensions that have been registered in configuration can be used like any other WCF component of the same type.</span></span>

##### <a name="adding-a-new-extension"></a><span data-ttu-id="09394-347">Adicionando uma nova extensão</span><span class="sxs-lookup"><span data-stu-id="09394-347">Adding a new extension</span></span>

<span data-ttu-id="09394-348">Selecione um dos nós de extensão nos nós avançados:</span><span class="sxs-lookup"><span data-stu-id="09394-348">Select one of the extension nodes in the advanced nodes:</span></span>

1. <span data-ttu-id="09394-349">Clique em **Novo**.</span><span class="sxs-lookup"><span data-stu-id="09394-349">Click **New**.</span></span>

2. <span data-ttu-id="09394-350">Insira um nome e um tipo.</span><span class="sxs-lookup"><span data-stu-id="09394-350">Enter a name and type.</span></span>

3. <span data-ttu-id="09394-351">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="09394-351">Click **OK**.</span></span>

4. <span data-ttu-id="09394-352">A extensão agora aparece no local apropriado no editor.</span><span class="sxs-lookup"><span data-stu-id="09394-352">The extension now appears in the appropriate place in the Editor.</span></span> <span data-ttu-id="09394-353">Por exemplo, se você adicionar uma extensão de elemento de comportamento, ela aparecerá na lista de extensões disponíveis.</span><span class="sxs-lookup"><span data-stu-id="09394-353">For example, if you add a behavior element extension, it appears in the list of available extensions.</span></span>

#### <a name="hosting-environment"></a><span data-ttu-id="09394-354">Ambiente de hospedagem</span><span class="sxs-lookup"><span data-stu-id="09394-354">Hosting Environment</span></span>

<span data-ttu-id="09394-355">Esta seção permite que você defina as configurações de instanciação para o ambiente de Hospedagem de serviço.</span><span class="sxs-lookup"><span data-stu-id="09394-355">This section allows you to define instantiation settings for the service hosting environment.</span></span>

### <a name="creating-a-configuration-file-using-the-wizard"></a><span data-ttu-id="09394-356">Criando um arquivo de configuração usando o assistente</span><span class="sxs-lookup"><span data-stu-id="09394-356">Creating a Configuration File Using the Wizard</span></span>

<span data-ttu-id="09394-357">Uma maneira de criar um novo arquivo de configuração é usar o assistente de novo elemento de serviço.</span><span class="sxs-lookup"><span data-stu-id="09394-357">One way to create a new configuration file is to use the New Service Element Wizard.</span></span> <span data-ttu-id="09394-358">O assistente localiza os tipos de serviço instalados e outros elementos compatíveis com o WCF no computador, incluindo diretórios virtuais do COM+ e hospedados na Web, e os carrega para tornar a criação da configuração muito mais simplificada.</span><span class="sxs-lookup"><span data-stu-id="09394-358">The wizard finds the installed service types and other elements compatible with WCF on the computer, including COM+ and Web-hosted virtual directories, and loads them to make creating the configuration much more streamlined.</span></span>

#### <a name="creating-a-configuration-file"></a><span data-ttu-id="09394-359">Criando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="09394-359">Creating a Configuration File</span></span>

1. <span data-ttu-id="09394-360">Inicie o editor de configuração de serviço usando uma janela de comando para navegar até o local de instalação do WCF e digite `SvcConfigEditor.exe`.</span><span class="sxs-lookup"><span data-stu-id="09394-360">Start Service Configuration Editor by using a command window to navigate to your WCF installation location, and then type `SvcConfigEditor.exe`.</span></span>

2. <span data-ttu-id="09394-361">No menu **arquivo** , selecione **abrir** e clique em **executável**, **serviço com+** ou **serviço Webhost**, dependendo do tipo de arquivo de configuração que você deseja criar.</span><span class="sxs-lookup"><span data-stu-id="09394-361">From the **File** menu, select **Open** and click **Executable**, **COM+ Service**, or **WebHosted Service**, depending on the type of configuration file you want to create.</span></span>

3. <span data-ttu-id="09394-362">Na caixa de diálogo **abrir** , navegue até o arquivo específico para o qual você deseja criar um arquivo de configuração e clique duas vezes nele.</span><span class="sxs-lookup"><span data-stu-id="09394-362">In the **Open** dialog box, navigate to the specific file you want to create a configuration file for and double-click it.</span></span>

4. <span data-ttu-id="09394-363">No menu **arquivo** , aponte para **Adicionar novo item** e clique em **serviço**.</span><span class="sxs-lookup"><span data-stu-id="09394-363">In the **File** menu, point to **Add New Item** and click **Service**.</span></span> <span data-ttu-id="09394-364">O assistente de novo elemento de serviço é aberto.</span><span class="sxs-lookup"><span data-stu-id="09394-364">The New Service Element Wizard opens.</span></span>

5. <span data-ttu-id="09394-365">Siga as etapas no Assistente para criar o novo serviço.</span><span class="sxs-lookup"><span data-stu-id="09394-365">Follow the steps in the wizard to create the new service.</span></span>

> [!NOTE]
> <span data-ttu-id="09394-366">Se você quiser usar o NetPeerTcpBinding do arquivo de configuração gerado pelo assistente, será necessário adicionar manualmente um elemento de configuração de associação e modificar o atributo `mode` de seu elemento `security` para "nenhum".</span><span class="sxs-lookup"><span data-stu-id="09394-366">If you want to use the NetPeerTcpBinding from the configuration file generated by the Wizard, you have to manually add a binding configuration element and modify the `mode` attribute of its `security` element to "None".</span></span>

## <a name="configuring-com"></a><span data-ttu-id="09394-367">Configurando COM+</span><span class="sxs-lookup"><span data-stu-id="09394-367">Configuring COM+</span></span>

<span data-ttu-id="09394-368">O editor de configuração de serviço permite que você crie um novo arquivo de configuração para um aplicativo existente do COM+ ou edite uma configuração existente do COM+.</span><span class="sxs-lookup"><span data-stu-id="09394-368">The Service Configuration Editor enables you to create a new configuration file for an existing COM+ application, or edit an existing COM+ configuration.</span></span> <span data-ttu-id="09394-369">O nó do **contrato com** só fica visível quando a seção < `comContract` > existe no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="09394-369">The **COM Contract** node is only visible when the <`comContract`> section exists in the configuration file.</span></span>

### <a name="creating-a-new-com-configuration"></a><span data-ttu-id="09394-370">Criando uma nova configuração COM+</span><span class="sxs-lookup"><span data-stu-id="09394-370">Creating a New COM+ Configuration</span></span>

<span data-ttu-id="09394-371">Antes de criar uma nova configuração COM+, verifique se seu aplicativo COM+ está instalado nos serviços de componentes e registrado no GAC (cache de assembly global).</span><span class="sxs-lookup"><span data-stu-id="09394-371">Before creating a new COM+ configuration, make sure that your COM+ application is installed in Component Services, and registered in the Global Assembly Cache (GAC).</span></span>

1. <span data-ttu-id="09394-372">Selecione o menu **arquivo** -> **integre**o aplicativo  -> **com+.**</span><span class="sxs-lookup"><span data-stu-id="09394-372">Select **File** menu -> **Integrate** -> **COM+ Application.**</span></span> <span data-ttu-id="09394-373">Esta operação fecha o arquivo aberto atual.</span><span class="sxs-lookup"><span data-stu-id="09394-373">This operation closes the current opened file.</span></span> <span data-ttu-id="09394-374">Se houver dados não salvos no arquivo atual, uma caixa de diálogo Salvar será exibida.</span><span class="sxs-lookup"><span data-stu-id="09394-374">If there is unsaved data in the current file, a Save dialog appears.</span></span> <span data-ttu-id="09394-375">O **Assistente de integração com+** é então iniciado.</span><span class="sxs-lookup"><span data-stu-id="09394-375">The **COM+ Integration Wizard** is then launched.</span></span>

2. <span data-ttu-id="09394-376">Na primeira página, selecione o aplicativo COM+ na árvore.</span><span class="sxs-lookup"><span data-stu-id="09394-376">In the first page, select the COM+ application from the tree.</span></span> <span data-ttu-id="09394-377">Se você não encontrar seu aplicativo COM+ na árvore, verifique se ele está instalado nos serviços de componentes e registrado no GAC (cache de assembly global).</span><span class="sxs-lookup"><span data-stu-id="09394-377">If you cannot find your COM+ application in the tree, verify that it is installed in the Component Services and registered in the Global Assembly Cache (GAC).</span></span>

3. <span data-ttu-id="09394-378">Na próxima página, selecione quais métodos você deseja expor como serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="09394-378">In the next page, select which method(s) you want to expose as WCF services.</span></span> <span data-ttu-id="09394-379">Todos os métodos com suporte no aplicativo COM+ são exibidos e selecionados por padrão.</span><span class="sxs-lookup"><span data-stu-id="09394-379">All the supported methods in the COM+ application are displayed and selected by default.</span></span>

4. <span data-ttu-id="09394-380">Escolha um método de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="09394-380">Choose a hosting method.</span></span>

5. <span data-ttu-id="09394-381">Defina outras configurações de acordo com os guias do assistente.</span><span class="sxs-lookup"><span data-stu-id="09394-381">Configure other settings according to the guides in the wizard.</span></span>

6. <span data-ttu-id="09394-382">O editor de configuração de serviço utiliza ComSvcConfig. exe em segundo plano para gerar o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="09394-382">Service Configuration Editor utilizes ComSvcConfig.exe in the background to generate configuration file.</span></span> <span data-ttu-id="09394-383">Depois que isso for concluído, você poderá exibir um resumo e sair do assistente.</span><span class="sxs-lookup"><span data-stu-id="09394-383">After this is completed, you can view a summary and exit the wizard.</span></span> <span data-ttu-id="09394-384">O arquivo de configuração gerado é aberto para que você possa editá-lo diretamente.</span><span class="sxs-lookup"><span data-stu-id="09394-384">The generated configuration file is opened so that you can edit it directly.</span></span>

### <a name="editing-an-existing-com-configuration"></a><span data-ttu-id="09394-385">Editando uma configuração COM+ existente</span><span class="sxs-lookup"><span data-stu-id="09394-385">Editing an Existing COM+ Configuration</span></span>

1. <span data-ttu-id="09394-386">Selecione o menu **arquivo** -> **abrir**o serviço  -> **com+** ...</span><span class="sxs-lookup"><span data-stu-id="09394-386">Select **File** menu -> **Open** -> **COM+ Service**…</span></span>

2. <span data-ttu-id="09394-387">Selecione o serviço COM+ que você deseja editar na lista.</span><span class="sxs-lookup"><span data-stu-id="09394-387">Select the COM+ Service you want to edit from the list.</span></span>

3. <span data-ttu-id="09394-388">Edite as definições de configuração no nó **contratos com** .</span><span class="sxs-lookup"><span data-stu-id="09394-388">Edit configuration settings in the **COM Contracts** node.</span></span>

    > [!NOTE]
    > <span data-ttu-id="09394-389">Você também pode abrir e editar diretamente um arquivo de configuração que contenha contratos COM.</span><span class="sxs-lookup"><span data-stu-id="09394-389">You can also directly open and edit a configuration file that contains COM contracts.</span></span>

## <a name="security"></a><span data-ttu-id="09394-390">Segurança</span><span class="sxs-lookup"><span data-stu-id="09394-390">Security</span></span>

<span data-ttu-id="09394-391">Não há garantia de que um arquivo de configuração de serviço gerado pelo editor de configuração seja seguro.</span><span class="sxs-lookup"><span data-stu-id="09394-391">A service configuration file generated by the Configuration Editor is not guaranteed to be secure.</span></span> <span data-ttu-id="09394-392">Consulte a documentação de [segurança](./feature-details/security.md) para saber como proteger seus serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="09394-392">Please refer to the [Security](./feature-details/security.md) documentation to find out how to secure your WCF services.</span></span>

<span data-ttu-id="09394-393">Além disso, o editor de configuração só pode ser usado para ler e gravar elementos válidos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="09394-393">In addition, the Configuration Editor can only be used to read and write valid WCF configuration elements.</span></span> <span data-ttu-id="09394-394">A ferramenta ignora elementos definidos pelo usuário em conformidade com o esquema.</span><span class="sxs-lookup"><span data-stu-id="09394-394">The tool ignores schema-compliant, user-defined elements.</span></span> <span data-ttu-id="09394-395">Ele também não tenta remover esses elementos do arquivo de configuração ou determinar seus efeitos nos elementos conhecidos do WCF.</span><span class="sxs-lookup"><span data-stu-id="09394-395">It also does not attempt remove these elements from the configuration file or determine their effects on the known WCF elements.</span></span> <span data-ttu-id="09394-396">É responsabilidade do usuário determinar se esses elementos representam uma ameaça ao aplicativo ou ao sistema.</span><span class="sxs-lookup"><span data-stu-id="09394-396">It is the user’s responsibility to determine whether these elements pose a threat to the application or the system.</span></span>
