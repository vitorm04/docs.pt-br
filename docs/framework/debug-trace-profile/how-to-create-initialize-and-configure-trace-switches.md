---
title: 'Como: criar, inicializar e configurar opções de rastreamento'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace switches, configuring
- tracing [.NET Framework], trace switches
- switches, trace
- tracing [.NET Framework], enabling or disabling
- Web.config configuration file, trace switches
ms.assetid: 5a0e41bf-f99c-4692-8799-f89617f5bcf9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 87170035df47e7605d25531df4b0759bf121ad80
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754343"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a><span data-ttu-id="6ca39-102">Como: criar, inicializar e configurar opções de rastreamento</span><span class="sxs-lookup"><span data-stu-id="6ca39-102">How to: Create, Initialize and Configure Trace Switches</span></span>
<span data-ttu-id="6ca39-103">As opções de rastreamento permitem habilitar, desabilitar e filtrar a saída de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6ca39-103">Trace switches enable you to enable, disable, and filter tracing output.</span></span>  
  
<a name="create"></a>   
## <a name="creating-and-initializing-a-trace-switch"></a><span data-ttu-id="6ca39-104">Criando e inicializando uma opção de rastreamento</span><span class="sxs-lookup"><span data-stu-id="6ca39-104">Creating and initializing a trace switch</span></span>  
 <span data-ttu-id="6ca39-105">Para usar opções de rastreamento, primeiro você deve criá-las e colocá-las no código.</span><span class="sxs-lookup"><span data-stu-id="6ca39-105">In order to use trace switches, you must first create them and place them in your code.</span></span> <span data-ttu-id="6ca39-106">Há duas classes predefinidas com base nas quais você pode criar objetos de opção: a classe <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> e a classe <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6ca39-106">There are two predefined classes from which you can create switch objects: the <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> class and the <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="6ca39-107">Use <xref:System.Diagnostics.BooleanSwitch> se você se importar apenas com o fato de uma mensagem de rastreamento ser exibida ou não; use <xref:System.Diagnostics.TraceSwitch> se desejar discriminar entre níveis de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6ca39-107">You would use <xref:System.Diagnostics.BooleanSwitch> if you care only about whether or not a tracing message appears; you would use <xref:System.Diagnostics.TraceSwitch> if you want to discriminate between levels of tracing.</span></span> <span data-ttu-id="6ca39-108">Se você usar uma <xref:System.Diagnostics.TraceSwitch>, poderá definir suas próprias mensagens de depuração e associá-las a diferentes níveis de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6ca39-108">If you use a <xref:System.Diagnostics.TraceSwitch>, you can define your own debugging messages and associate them with different trace levels.</span></span> <span data-ttu-id="6ca39-109">Use ambos os tipos de opções com o rastreamento ou a depuração.</span><span class="sxs-lookup"><span data-stu-id="6ca39-109">You can use both types of switches with either tracing or debugging.</span></span> <span data-ttu-id="6ca39-110">Por padrão, uma <xref:System.Diagnostics.BooleanSwitch> está desabilitada e uma <xref:System.Diagnostics.TraceSwitch> está definida como o nível <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6ca39-110">By default, a <xref:System.Diagnostics.BooleanSwitch> is disabled and a <xref:System.Diagnostics.TraceSwitch> is set to level <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6ca39-111">As opções de rastreamento podem ser criadas e colocadas em qualquer parte do código que você pode usá-las.</span><span class="sxs-lookup"><span data-stu-id="6ca39-111">Trace switches can be created and placed in any part of your code that might use them.</span></span>  
  
 <span data-ttu-id="6ca39-112">Embora seja possível definir níveis de rastreamento e outras opções de configuração no código, recomendamos o uso do arquivo de configuração para gerenciar o estado das opções.</span><span class="sxs-lookup"><span data-stu-id="6ca39-112">Although you can set trace levels and other configuration options in code, we recommend that you use the configuration file to manage the state of your switches.</span></span> <span data-ttu-id="6ca39-113">Isso ocorre porque o gerenciamento da configuração das opções no sistema de configuração proporciona maior flexibilidade – você pode ativar e desativar várias opções e alterar os níveis sem recompilar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6ca39-113">This is because managing the configuration of your switches in the configuration system gives you greater flexibility — you can turn on and off various switches and change levels without recompiling your application.</span></span>  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a><span data-ttu-id="6ca39-114">Para criar e inicializar uma opção de rastreamento</span><span class="sxs-lookup"><span data-stu-id="6ca39-114">To create and initialize a trace switch</span></span>  
  
1. <span data-ttu-id="6ca39-115">Defina uma opção como o tipo <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> ou o tipo <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> e defina o nome e a descrição da opção.</span><span class="sxs-lookup"><span data-stu-id="6ca39-115">Define a switch as either type <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> or type <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> and set the name and description of the switch.</span></span>  
  
2. <span data-ttu-id="6ca39-116">Configure a opção de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="6ca39-116">Configure your trace switch.</span></span> <span data-ttu-id="6ca39-117">Para obter mais informações, consulte [Configurando opções de rastreamento](#configure).</span><span class="sxs-lookup"><span data-stu-id="6ca39-117">For more information, see [Configuring trace switches](#configure).</span></span>  
  
     <span data-ttu-id="6ca39-118">O código a seguir cria duas opções, uma de cada tipo:</span><span class="sxs-lookup"><span data-stu-id="6ca39-118">The following code creates two switches, one of each type:</span></span>  
  
    ```vb  
    Dim dataSwitch As New BooleanSwitch("Data", "DataAccess module")  
    Dim generalSwitch As New TraceSwitch("General", "Entire application")  
    ```  
  
    ```csharp  
    System.Diagnostics.BooleanSwitch dataSwitch =   
       new System.Diagnostics.BooleanSwitch("Data", "DataAccess module");  
    System.Diagnostics.TraceSwitch generalSwitch =   
       new System.Diagnostics.TraceSwitch("General",   
       "Entire application");  
    ```  
  
<a name="configure"></a>   
## <a name="configuring-trace-switches"></a><span data-ttu-id="6ca39-119">Configurando opções de rastreamento</span><span class="sxs-lookup"><span data-stu-id="6ca39-119">Configuring trace switches</span></span>  
 <span data-ttu-id="6ca39-120">Depois que o aplicativo for distribuído, você ainda poderá habilitar ou desabilitar a saída de rastreamento configurando as opções de rastreamento no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6ca39-120">After your application has been distributed, you can still enable or disable trace output by configuring the trace switches in your application.</span></span> <span data-ttu-id="6ca39-121">A configuração de uma opção significa alterar seu valor de uma fonte externa, depois que ela foi inicializada.</span><span class="sxs-lookup"><span data-stu-id="6ca39-121">Configuring a switch means changing its value from an external source after it has been initialized.</span></span> <span data-ttu-id="6ca39-122">Você pode alterar os valores dos objetos de opção usando o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="6ca39-122">You can change the values of the switch objects using the configuration file.</span></span> <span data-ttu-id="6ca39-123">Configure uma opção de rastreamento para ativá-la e desativá-la ou para definir seu nível, determinando a quantidade e o tipo de mensagens que são passados para os ouvintes.</span><span class="sxs-lookup"><span data-stu-id="6ca39-123">You configure a trace switch to turn it on and off, or to set its level, determining the amount and type of messages it passes along to listeners.</span></span>  
  
 <span data-ttu-id="6ca39-124">As opções são configuradas usando o arquivo .config.</span><span class="sxs-lookup"><span data-stu-id="6ca39-124">Your switches are configured using the .config file.</span></span> <span data-ttu-id="6ca39-125">Para um aplicativo Web, este é o arquivo Web.config associado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="6ca39-125">For a Web application, this is the Web.config file associated with the project.</span></span> <span data-ttu-id="6ca39-126">Em um aplicativo do Windows, esse arquivo é chamado (nome do aplicativo).exe.config. Em um aplicativo implantado, esse arquivo deve residir na mesma pasta do executável.</span><span class="sxs-lookup"><span data-stu-id="6ca39-126">In a Windows application, this file is named (application name).exe.config. In a deployed application, this file must reside in the same folder as the executable.</span></span>  
  
 <span data-ttu-id="6ca39-127">Quando o aplicativo executa o código que cria uma instância de uma opção pela primeira vez, ele verifica o arquivo de configuração para obter informações no nível do rastreamento sobre a opção nomeada.</span><span class="sxs-lookup"><span data-stu-id="6ca39-127">When your application executes the code that creates an instance of a switch for the first time, it checks the configuration file for trace-level information about the named switch.</span></span> <span data-ttu-id="6ca39-128">O sistema de rastreamento examina o arquivo de configuração apenas uma vez em busca de uma opção específica – na primeira vez que o aplicativo cria o objeto.</span><span class="sxs-lookup"><span data-stu-id="6ca39-128">The tracing system examines the configuration file only once for any particular switch — the first time your application creates the switch.</span></span>  
  
 <span data-ttu-id="6ca39-129">Em um aplicativo implantado, habilite o código de rastreamento reconfigurando objetos de opção quando o aplicativo não estiver em execução.</span><span class="sxs-lookup"><span data-stu-id="6ca39-129">In a deployed application, you enable trace code by reconfiguring switch objects when your application is not running.</span></span> <span data-ttu-id="6ca39-130">Normalmente, isso envolve a ativação e desativação dos objetos de opção ou a alteração dos níveis de rastreamento e, em seguida, a reinicialização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6ca39-130">Typically this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>  
  
 <span data-ttu-id="6ca39-131">Quando você cria uma instância com base em uma opção, você também inicializa-a com a especificação de dois argumentos: um argumento *displayName* e um argumento *description*.</span><span class="sxs-lookup"><span data-stu-id="6ca39-131">When you create an instance of a switch, you also initialize it by specifying two arguments: a *displayName* argument and a *description* argument.</span></span> <span data-ttu-id="6ca39-132">O argumento *displayName* do construtor define a propriedade <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> da instância da classe <xref:System.Diagnostics.Switch>.</span><span class="sxs-lookup"><span data-stu-id="6ca39-132">The *displayName* argument of the constructor sets the <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> property of the <xref:System.Diagnostics.Switch> class instance.</span></span> <span data-ttu-id="6ca39-133">O *displayName* é o nome usado para configurar a opção no arquivo .config e o argumento *description* deve retornar uma breve descrição da opção e quais mensagens são controladas por ela.</span><span class="sxs-lookup"><span data-stu-id="6ca39-133">The *displayName* is the name that is used to configure the switch in the .config file, and the *description* argument should return a brief description of the switch and what messages it controls.</span></span>  
  
 <span data-ttu-id="6ca39-134">Além de especificar o nome de uma opção a ser configurada, você também deve especificar um valor para a opção.</span><span class="sxs-lookup"><span data-stu-id="6ca39-134">In addition to specifying the name of a switch to configure, you must also specify a value for the switch.</span></span> <span data-ttu-id="6ca39-135">Esse valor é um Inteiro.</span><span class="sxs-lookup"><span data-stu-id="6ca39-135">This value is an Integer.</span></span> <span data-ttu-id="6ca39-136">Para <xref:System.Diagnostics.BooleanSwitch>, um valor igual a 0 corresponde a **Off** e qualquer valor diferente de zero corresponde a **On**.</span><span class="sxs-lookup"><span data-stu-id="6ca39-136">For <xref:System.Diagnostics.BooleanSwitch>, a value of 0 corresponds to **Off**, and any nonzero value corresponds to **On**.</span></span> <span data-ttu-id="6ca39-137">Para <xref:System.Diagnostics.TraceSwitch>, 0, 1, 2, 3 e 4 correspondem a **Off**, **Error**, **Warning**, **Info** e **Verbose**, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="6ca39-137">For <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3, and 4 correspond **Off**, **Error**, **Warning**, **Info**, and **Verbose**, respectively.</span></span> <span data-ttu-id="6ca39-138">Qualquer número maior que 4 é tratado como **Verbose** e qualquer número menor que zero é tratado como **Off**.</span><span class="sxs-lookup"><span data-stu-id="6ca39-138">Any number greater than 4 is treated as **Verbose**, and any number less than zero is treated as **Off**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6ca39-139">No .NET Framework versão 2.0, você pode usar o texto para especificar o valor de uma opção.</span><span class="sxs-lookup"><span data-stu-id="6ca39-139">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="6ca39-140">Por exemplo, `true` para uma <xref:System.Diagnostics.BooleanSwitch> ou o texto que representa um valor de enumeração como `Error` para uma <xref:System.Diagnostics.TraceSwitch>.</span><span class="sxs-lookup"><span data-stu-id="6ca39-140">For example, `true` for a <xref:System.Diagnostics.BooleanSwitch> or the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="6ca39-141">A linha `<add name="myTraceSwitch" value="Error" />` é equivalente a `<add name="myTraceSwitch" value="1" />`.</span><span class="sxs-lookup"><span data-stu-id="6ca39-141">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
 <span data-ttu-id="6ca39-142">Para que os usuários finais possam definir as opções de rastreamento de um aplicativo, você deve fornecer uma documentação detalhada das opções no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6ca39-142">In order for end users to be able to configure an application's trace switches, you must provide detailed documentation on the switches in your application.</span></span> <span data-ttu-id="6ca39-143">É necessário fornecer detalhes sobre quais opções controlam o que e como ativá-las e desativá-las.</span><span class="sxs-lookup"><span data-stu-id="6ca39-143">You should detail which switches control what and how to turn them on and off.</span></span> <span data-ttu-id="6ca39-144">Você também deve fornecer ao usuário final um arquivo .config que tem a Ajuda apropriada nos comentários.</span><span class="sxs-lookup"><span data-stu-id="6ca39-144">You should also provide your end user with a .config file that has appropriate Help in the comments.</span></span>  
  
#### <a name="to-configure-trace-switches"></a><span data-ttu-id="6ca39-145">Para configurar opções de rastreamento</span><span class="sxs-lookup"><span data-stu-id="6ca39-145">To configure trace switches</span></span>  
  
1. <span data-ttu-id="6ca39-146">Para usar opções de rastreamento, primeiro você deve criá-las e colocá-las no código, conforme descrito na seção [Criando e inicializando uma opção de rastreamento](#create).</span><span class="sxs-lookup"><span data-stu-id="6ca39-146">In order to use trace switches, you must first create them and place them in your code as described in the section [Creating and initializing a trace switch](#create).</span></span>  
  
2. <span data-ttu-id="6ca39-147">Se o projeto não contiver um arquivo de configuração (app.config ou Web.config), no menu **Projeto**, selecione **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="6ca39-147">If your project does not contain a configuration file (app.config or Web.config), then from the **Project** menu, select **Add New Item**.</span></span>  
  
    - <span data-ttu-id="6ca39-148">**Visual Basic:** No **Adicionar Novo Item** diálogo caixa, escolha **arquivo de configuração de aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="6ca39-148">**Visual Basic:** In the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
         <span data-ttu-id="6ca39-149">O arquivo de configuração de aplicativo será criado e aberto.</span><span class="sxs-lookup"><span data-stu-id="6ca39-149">The application configuration file is created and opened.</span></span> <span data-ttu-id="6ca39-150">Este é um documento XML cujo elemento raiz é `<configuration>.`</span><span class="sxs-lookup"><span data-stu-id="6ca39-150">This is an XML document whose root element is `<configuration>.`</span></span>  
  
    - <span data-ttu-id="6ca39-151">**Visual C#:** No **Adicionar Novo Item** diálogo caixa, escolha **arquivo XML**.</span><span class="sxs-lookup"><span data-stu-id="6ca39-151">**Visual C#:** In the **Add New Item** dialog box, choose **XML File**.</span></span> <span data-ttu-id="6ca39-152">Nomeie esse arquivo **app.config**. No editor de XML, após a declaração XML, adicione o seguinte XML:</span><span class="sxs-lookup"><span data-stu-id="6ca39-152">Name this file **app.config**. In the XML editor, after the XML declaration, add the following XML:</span></span>  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         <span data-ttu-id="6ca39-153">Quando o projeto é compilado, o arquivo app.config é copiado para a pasta de saída do projeto e é renomeado *applicationname*.exe.config.</span><span class="sxs-lookup"><span data-stu-id="6ca39-153">When your project is compiled, the app.config file is copied to the project output folder and is renamed *applicationname*.exe.config.</span></span>  
  
3. <span data-ttu-id="6ca39-154">Após a marcação `<configuration>`, mas antes da marcação `</configuration>`, adicione o XML apropriado para configurar as opções.</span><span class="sxs-lookup"><span data-stu-id="6ca39-154">After the `<configuration>` tag but before the `</configuration>` tag, add the appropriate XML to configure your switches.</span></span> <span data-ttu-id="6ca39-155">Os exemplos a seguir demonstram uma **BooleanSwitch** com uma propriedade **DisplayName** `DataMessageSwitch` e uma **TraceSwitch** com uma propriedade **DisplayName** igual a `TraceLevelSwitch`.</span><span class="sxs-lookup"><span data-stu-id="6ca39-155">The following examples demonstrate a **BooleanSwitch** with a **DisplayName** property of `DataMessageSwitch` and a **TraceSwitch** with a **DisplayName** property of `TraceLevelSwitch`.</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     <span data-ttu-id="6ca39-156">Nessa configuração, ambas as opções estão desativadas.</span><span class="sxs-lookup"><span data-stu-id="6ca39-156">In this configuration, both switches are off.</span></span>  
  
4. <span data-ttu-id="6ca39-157">Se precisar ativar uma **BooleanSwitch**, como `DataMessagesSwitch` mostrado no exemplo anterior, altere o **Value** para qualquer inteiro diferente de 0.</span><span class="sxs-lookup"><span data-stu-id="6ca39-157">If you need to turn on a **BooleanSwitch**, such as `DataMessagesSwitch` shown in the previous example, change the **Value** to any integer other than 0.</span></span>  
  
5. <span data-ttu-id="6ca39-158">Se precisar ativar uma **TraceSwitch**, como `TraceLevelSwitch` mostrado no exemplo anterior, altere o **Value** para a configuração de nível apropriada (1 a 4).</span><span class="sxs-lookup"><span data-stu-id="6ca39-158">If you need to turn on a **TraceSwitch**, such as `TraceLevelSwitch` shown in the previous example, change the **Value** to the appropriate level setting (1 to 4).</span></span>  
  
6. <span data-ttu-id="6ca39-159">Adicione comentários ao arquivo .config, de modo que o usuário final tenha uma compreensão clara dos valores que devem ser alterados para configurar as opções de forma adequada.</span><span class="sxs-lookup"><span data-stu-id="6ca39-159">Add comments to the .config file so the end user has a clear understanding of what values to change to configure the switches appropriately.</span></span>  
  
     <span data-ttu-id="6ca39-160">O seguinte exemplo mostra a possível aparência do código final, incluindo comentários:</span><span class="sxs-lookup"><span data-stu-id="6ca39-160">The following example shows how the final code, including comments, might look:</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <!-- This switch controls data messages. In order to receive data   
             trace messages, change value="0" to value="1" -->  
          <add name="DataMessagesSwitch" value="0" />  
          <!-- This switch controls general messages. In order to   
             receive general trace messages change the value to the   
             appropriate level. "1" gives error messages, "2" gives errors   
             and warnings, "3" gives more detailed error information, and   
             "4" gives verbose trace information -->  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6ca39-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ca39-161">See also</span></span>

- [<span data-ttu-id="6ca39-162">Rastreando e instrumentando aplicativos</span><span class="sxs-lookup"><span data-stu-id="6ca39-162">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="6ca39-163">Como: Adicionar instruções de rastreamento ao código do aplicativo</span><span class="sxs-lookup"><span data-stu-id="6ca39-163">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="6ca39-164">Opções de rastreamento</span><span class="sxs-lookup"><span data-stu-id="6ca39-164">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="6ca39-165">Esquema de configurações de rastreamento e depuração</span><span class="sxs-lookup"><span data-stu-id="6ca39-165">Trace and Debug Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
