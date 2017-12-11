---
title: Criar ouvintes de log personalizados (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b1bda4a3465af4ed95de720117ea2e03f9a86b84
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="02c07-102">Instruções passo a passo: criando ouvintes de log personalizados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="02c07-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="02c07-103">Estas instruções passo a passo demonstram como criar um ouvinte de log personalizado e configurá-lo para ouvir a saída do objeto `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="02c07-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="02c07-104">Guia de Introdução</span><span class="sxs-lookup"><span data-stu-id="02c07-104">Getting Started</span></span>  
 <span data-ttu-id="02c07-105">Ouvintes de log devem herdar da classe <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="02c07-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
#### <a name="to-create-the-listener"></a><span data-ttu-id="02c07-106">Para criar o ouvinte</span><span class="sxs-lookup"><span data-stu-id="02c07-106">To create the listener</span></span>  
  
-   <span data-ttu-id="02c07-107">Em seu aplicativo, crie uma classe denominada `SimpleListener` que herda de <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="02c07-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#16](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_1.vb)]  
  
     <span data-ttu-id="02c07-108">Os métodos <xref:System.Diagnostics.TraceListener.Write%2A> e <xref:System.Diagnostics.TraceListener.WriteLine%2A>, exigidos pela classe base, chamam `MsgBox` para exibir sua entrada.</span><span class="sxs-lookup"><span data-stu-id="02c07-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>  
  
     <span data-ttu-id="02c07-109">O atributo <xref:System.Security.Permissions.HostProtectionAttribute> é aplicado aos métodos <xref:System.Diagnostics.TraceListener.Write%2A> e <xref:System.Diagnostics.TraceListener.WriteLine%2A> para que seus atributos coincidam com os métodos da classe base.</span><span class="sxs-lookup"><span data-stu-id="02c07-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="02c07-110">O atributo <xref:System.Security.Permissions.HostProtectionAttribute> permite que o host que executa o código determine que o código expõe a sincronização de proteção de host.</span><span class="sxs-lookup"><span data-stu-id="02c07-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="02c07-111">O atributo <xref:System.Security.Permissions.HostProtectionAttribute> é eficaz somente em aplicativos não gerenciados que hospedam o Common Language Runtime e implementam a proteção de host, como o SQL Server.</span><span class="sxs-lookup"><span data-stu-id="02c07-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>  
  
 <span data-ttu-id="02c07-112">Para garantir que o `My.Application.Log` use o ouvinte de log, você deve nomear fortemente o assembly que contém o ouvinte de log.</span><span class="sxs-lookup"><span data-stu-id="02c07-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>  
  
 <span data-ttu-id="02c07-113">O procedimento seguinte fornece algumas etapas simples para criar um assembly de ouvinte de log de nome forte.</span><span class="sxs-lookup"><span data-stu-id="02c07-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="02c07-114">Para obter mais informações, consulte [Criando e usando assemblies de nomes fortes](../../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="02c07-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="02c07-115">Para nomear fortemente o assembly de ouvinte de log</span><span class="sxs-lookup"><span data-stu-id="02c07-115">To strongly name the log-listener assembly</span></span>  
  
1.  <span data-ttu-id="02c07-116">Selecione um projeto no **Gerenciador de Soluções**.</span><span class="sxs-lookup"><span data-stu-id="02c07-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="02c07-117">No menu **Projeto**, escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="02c07-117">On the **Project** menu, choose **Properties**.</span></span> <span data-ttu-id="02c07-118">Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="02c07-118">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span>  
  
2.  <span data-ttu-id="02c07-119">Clique na guia **Assinatura**.</span><span class="sxs-lookup"><span data-stu-id="02c07-119">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="02c07-120">Marque a caixa **Assinar o assembly**.</span><span class="sxs-lookup"><span data-stu-id="02c07-120">Select the **Sign the assembly** box.</span></span>  
  
4.  <span data-ttu-id="02c07-121">Selecione **Novo\<** da lista suspensa **Escolha um arquivo de chave de nome forte**.</span><span class="sxs-lookup"><span data-stu-id="02c07-121">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>  
  
     <span data-ttu-id="02c07-122">A caixa de diálogo **Criar Chave de Nome Forte** é aberta.</span><span class="sxs-lookup"><span data-stu-id="02c07-122">The **Create Strong Name Key** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="02c07-123">Forneça um nome para o arquivo de chaves na caixa **Nome de arquivo de chaves**.</span><span class="sxs-lookup"><span data-stu-id="02c07-123">Provide a name for the key file in the **Key file name** box.</span></span>  
  
6.  <span data-ttu-id="02c07-124">Digite uma senha nas caixas **Digite a senha** e **Confirmar senha** caixas.</span><span class="sxs-lookup"><span data-stu-id="02c07-124">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>  
  
7.  <span data-ttu-id="02c07-125">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="02c07-125">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="02c07-126">Recompile o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="02c07-126">Rebuild the application.</span></span>  
  
## <a name="adding-the-listener"></a><span data-ttu-id="02c07-127">Adicionando o ouvinte</span><span class="sxs-lookup"><span data-stu-id="02c07-127">Adding the Listener</span></span>  
 <span data-ttu-id="02c07-128">Agora que o assembly tem um nome forte, você precisa determinar o nome forte do ouvinte para que `My.Application.Log` use seu ouvinte de log.</span><span class="sxs-lookup"><span data-stu-id="02c07-128">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>  
  
 <span data-ttu-id="02c07-129">O formato de um tipo de nome forte é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="02c07-129">The format of a strongly named type is as follows.</span></span>  
  
 <span data-ttu-id="02c07-130">\<nome do tipo>, \<nome do assembly>, \<número de versão>, \<cultura>, \<nome forte></span><span class="sxs-lookup"><span data-stu-id="02c07-130">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="02c07-131">Para determinar o nome forte do ouvinte</span><span class="sxs-lookup"><span data-stu-id="02c07-131">To determine the strong name of the listener</span></span>  
  
-   <span data-ttu-id="02c07-132">O código a seguir mostra como determinar o tipo de nome forte de `SimpleListener`.</span><span class="sxs-lookup"><span data-stu-id="02c07-132">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#17](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-creating-custom-log-listeners_2.vb)]  
  
     <span data-ttu-id="02c07-133">O nome forte do tipo depende de seu projeto.</span><span class="sxs-lookup"><span data-stu-id="02c07-133">The strong name of the type depends on your project.</span></span>  
  
 <span data-ttu-id="02c07-134">Com o nome forte, você pode adicionar o ouvinte à coleção de ouvintes de log `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="02c07-134">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="02c07-135">Para adicionar o ouvinte a My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="02c07-135">To add the listener to My.Application.Log</span></span>  
  
1.  <span data-ttu-id="02c07-136">Clique com o botão direito do mouse em app.config no **Gerenciador de Soluções** e escolha **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="02c07-136">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="02c07-137">-ou-</span><span class="sxs-lookup"><span data-stu-id="02c07-137">-or-</span></span>  
  
     <span data-ttu-id="02c07-138">Se houver um arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="02c07-138">If there is an app.config file:</span></span>  
  
    1.  <span data-ttu-id="02c07-139">No menu **Projeto**, escolha **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="02c07-139">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="02c07-140">Na caixa de diálogo **Adicionar novo item**, escolha **Arquivo de configuração de aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="02c07-140">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="02c07-141">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="02c07-141">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="02c07-142">Localize a seção `<listeners>`, na seção `<source>` com o `name` atributo "DefaultSource", localizado na seção `<sources>`.</span><span class="sxs-lookup"><span data-stu-id="02c07-142">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="02c07-143">A seção `<sources>` está localizada na seção `<system.diagnostics>`, na seção `<configuration>` superior.</span><span class="sxs-lookup"><span data-stu-id="02c07-143">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="02c07-144">Adicione esse elemento à seção `<listeners>`:</span><span class="sxs-lookup"><span data-stu-id="02c07-144">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4.  <span data-ttu-id="02c07-145">Localize a seção `<sharedListeners>`, na seção `<system.diagnostics>`, na seção `<configuration>` superior.</span><span class="sxs-lookup"><span data-stu-id="02c07-145">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="02c07-146">Adicione esse elemento a essa seção `<sharedListeners>`:</span><span class="sxs-lookup"><span data-stu-id="02c07-146">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     <span data-ttu-id="02c07-147">Altere o valor de `SimpleLogStrongName` para ser o nome forte do ouvinte.</span><span class="sxs-lookup"><span data-stu-id="02c07-147">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02c07-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02c07-148">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 [<span data-ttu-id="02c07-149">Trabalhando com logs de aplicativo</span><span class="sxs-lookup"><span data-stu-id="02c07-149">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="02c07-150">Como registrar em log as exceções</span><span class="sxs-lookup"><span data-stu-id="02c07-150">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [<span data-ttu-id="02c07-151">Como gravar mensagens de log</span><span class="sxs-lookup"><span data-stu-id="02c07-151">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [<span data-ttu-id="02c07-152">Instruções passo a passo: alterando onde My.Application.Log grava informações</span><span class="sxs-lookup"><span data-stu-id="02c07-152">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
