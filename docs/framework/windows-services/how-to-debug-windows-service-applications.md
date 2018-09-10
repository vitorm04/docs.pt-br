---
title: Como depurar aplicativos de Serviço Windows
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows NT services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
author: ghogen
manager: douge
ms.openlocfilehash: a0c57ab049fff699d5bb12004fd48d90a226e514
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525016"
---
# <a name="how-to-debug-windows-service-applications"></a><span data-ttu-id="90e9c-102">Como depurar aplicativos de Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="90e9c-102">How to: Debug Windows Service Applications</span></span>
<span data-ttu-id="90e9c-103">Um serviço deve ser executado de dentro do contexto do Gerenciador de Controle de Serviços, em vez de dentro do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="90e9c-103">A service must be run from within the context of the Services Control Manager rather than from within Visual Studio.</span></span> <span data-ttu-id="90e9c-104">Por esse motivo, depurar um serviço não é tão simples como depurar outros tipos de aplicativos do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="90e9c-104">For this reason, debugging a service is not as straightforward as debugging other Visual Studio application types.</span></span> <span data-ttu-id="90e9c-105">Para depurar um serviço, você deve iniciar o serviço e, em seguida, anexar um depurador ao processo no qual ele está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="90e9c-105">To debug a service, you must start the service and then attach a debugger to the process in which it is running.</span></span> <span data-ttu-id="90e9c-106">Em seguida, você pode depurar seu aplicativo usando todas as funcionalidades de depuração padrão do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="90e9c-106">You can then debug your application by using all of the standard debugging functionality of Visual Studio.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="90e9c-107">Você não deve anexá-lo a um processo, a menos que você saiba qual é o processo e entenda as consequências da anexação, possivelmente eliminando esse processo.</span><span class="sxs-lookup"><span data-stu-id="90e9c-107">You should not attach to a process unless you know what the process is and understand the consequences of attaching to and possibly killing that process.</span></span> <span data-ttu-id="90e9c-108">Por exemplo, se você anexá-lo ao processo WinLogon e interromper a depuração, o sistema será interrompido porque ele não pode operar sem o WinLogon.</span><span class="sxs-lookup"><span data-stu-id="90e9c-108">For example, if you attach to the WinLogon process and then stop debugging, the system will halt because it can’t operate without WinLogon.</span></span>  
  
 <span data-ttu-id="90e9c-109">Você pode anexar o depurador somente a um serviço em execução.</span><span class="sxs-lookup"><span data-stu-id="90e9c-109">You can attach the debugger only to a running service.</span></span> <span data-ttu-id="90e9c-110">O processo de anexação interrompe o funcionamento atual do seu serviço. Na verdade, ele não para ou pausa o processamento do serviço.</span><span class="sxs-lookup"><span data-stu-id="90e9c-110">The attachment process interrupts the current functioning of your service; it doesn’t actually stop or pause the service's processing.</span></span> <span data-ttu-id="90e9c-111">Ou seja, se o serviço está sendo executado quando você inicia a depuração, ele ainda está tecnicamente num estado inicial conforme você depura, mas seu processamento foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="90e9c-111">That is, if your service is running when you begin debugging, it is still technically in the Started state as you debug it, but its processing has been suspended.</span></span>  
  
 <span data-ttu-id="90e9c-112">Depois de anexá-lo ao processo, você pode definir pontos de interrupção e usá-los para depurar seu código.</span><span class="sxs-lookup"><span data-stu-id="90e9c-112">After attaching to the process, you can set breakpoints and use these to debug your code.</span></span> <span data-ttu-id="90e9c-113">Depois que sair da caixa de diálogo usada para anexá-lo ao processo, você estará efetivamente em modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="90e9c-113">Once you exit the dialog box you use to attach to the process, you are effectively in debug mode.</span></span> <span data-ttu-id="90e9c-114">Você pode usar o Gerenciador de Controle de Serviços para iniciar, parar, pausar e continuar seu serviço, alcançando, assim, os pontos de interrupção que você definiu.</span><span class="sxs-lookup"><span data-stu-id="90e9c-114">You can use the Services Control Manager to start, stop, pause and continue your service, thus hitting the breakpoints you've set.</span></span> <span data-ttu-id="90e9c-115">Posteriormente, você pode remover esse serviço fictício depois de depuração ser concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="90e9c-115">You can later remove this dummy service after debugging is successful.</span></span>  
  
 <span data-ttu-id="90e9c-116">Este artigo aborda a depuração de um serviço que está em execução no computador local, mas você também pode depurar serviços Windows que executados em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="90e9c-116">This article covers debugging a service that's running on the local computer, but you can also debug Windows Services that are running on a remote computer.</span></span> <span data-ttu-id="90e9c-117">Confira [Depuração remota](/visualstudio/debugger/debug-installed-app-package).</span><span class="sxs-lookup"><span data-stu-id="90e9c-117">See [Remote Debugging](/visualstudio/debugger/debug-installed-app-package).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90e9c-118">Depurar o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> pode ser difícil porque o Gerenciador de controle de Serviços impõe um limite de 30 segundos em todas as tentativas de iniciar um serviço.</span><span class="sxs-lookup"><span data-stu-id="90e9c-118">Debugging the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method can be difficult because the Services Control Manager imposes a 30-second limit on all attempts to start a service.</span></span> <span data-ttu-id="90e9c-119">Para obter mais informações, confira [Solução de problemas: depuração de Serviços Windows](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="90e9c-119">For more information, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="90e9c-120">Para obter informações significativas para depuração, o depurador do Visual Studio deve localizar os arquivos de símbolo para os binários que estão sendo depurados.</span><span class="sxs-lookup"><span data-stu-id="90e9c-120">To get meaningful information for debugging, the Visual Studio debugger needs to find symbol files for the binaries that are being debugged.</span></span> <span data-ttu-id="90e9c-121">Se você estiver depurando um serviço que você criou no Visual Studio, os arquivos de símbolo (arquivos .pdb) estarão na mesma pasta que o executável ou biblioteca, e o depurador os carregará automaticamente.</span><span class="sxs-lookup"><span data-stu-id="90e9c-121">If you are debugging a service that you built in Visual Studio, the symbol files (.pdb files) are in the same folder as the executable or library, and the debugger loads them automatically.</span></span> <span data-ttu-id="90e9c-122">Se você estiver depurando um serviço que não criou, deve primeiro localizar símbolos para o serviço e certificar-se de que eles podem ser encontrados pelo depurador.</span><span class="sxs-lookup"><span data-stu-id="90e9c-122">If you are debugging a service that you didn't build, you should first find symbols for the service and make sure they can be found by the debugger.</span></span> <span data-ttu-id="90e9c-123">Confira [Especificar arquivos de símbolo (.pdb) e de origem no Depurador do Visual Studio](https://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b).</span><span class="sxs-lookup"><span data-stu-id="90e9c-123">See [Specify Symbol (.pdb) and Source Files](https://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b).</span></span> <span data-ttu-id="90e9c-124">Se você estiver depurando um processo do sistema ou se desejar ter símbolos para chamadas do sistema em seus serviços, você deve adicionar os Servidores de Símbolo Microsoft.</span><span class="sxs-lookup"><span data-stu-id="90e9c-124">If you're debugging a system process or want to have symbols for system calls in your services, you should add the Microsoft Symbol Servers.</span></span> <span data-ttu-id="90e9c-125">Confira [Depurando símbolos](/windows/desktop/DxTechArts/debugging-with-symbols).</span><span class="sxs-lookup"><span data-stu-id="90e9c-125">See [Debugging Symbols](/windows/desktop/DxTechArts/debugging-with-symbols).</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="90e9c-126">Para depurar um serviço</span><span class="sxs-lookup"><span data-stu-id="90e9c-126">To debug a service</span></span>  
  
1.  <span data-ttu-id="90e9c-127">Crie seu serviço na configuração de depuração.</span><span class="sxs-lookup"><span data-stu-id="90e9c-127">Build your service in the Debug configuration.</span></span>  
  
2.  <span data-ttu-id="90e9c-128">Instalar o serviço.</span><span class="sxs-lookup"><span data-stu-id="90e9c-128">Install your service.</span></span> <span data-ttu-id="90e9c-129">Para obter mais informações, confira [Como instalar e desinstalar serviços](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="90e9c-129">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
3.  <span data-ttu-id="90e9c-130">Inicie o serviço, usando o **Gerenciador de Controle de Serviços**, o **Gerenciador de Servidores** ou o código.</span><span class="sxs-lookup"><span data-stu-id="90e9c-130">Start your service, either from **Services Control Manager**, **Server Explorer**, or from code.</span></span> <span data-ttu-id="90e9c-131">Para obter mais informações, confira [Como iniciar serviços](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="90e9c-131">For more information, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span>  
  
4.  <span data-ttu-id="90e9c-132">Inicie o Visual Studio com credenciais administrativas para que você possa se conectar aos processos do sistema.</span><span class="sxs-lookup"><span data-stu-id="90e9c-132">Start Visual Studio with administrative credentials so you can attach to system processes.</span></span>  
  
5.  <span data-ttu-id="90e9c-133">(Opcional) Na barra de menus do Visual Studio, escolha **Ferramentas**, **Opções**.</span><span class="sxs-lookup"><span data-stu-id="90e9c-133">(Optional) On the Visual Studio menu bar, choose **Tools**, **Options**.</span></span> <span data-ttu-id="90e9c-134">Na caixa de diálogo **Opções**, escolha **Depuração**, **Símbolos**, marque a caixa de seleção **Servidores de Símbolos da Microsoft** e, em seguida, clique no botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="90e9c-134">In the **Options** dialog box, choose **Debugging**, **Symbols**, select the **Microsoft Symbol Servers** check box, and then choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="90e9c-135">Na barra de menus, escolha **Anexar ao Processo** no menu **Depurar** ou **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="90e9c-135">On the menu bar, choose **Attach to Process** from the **Debug** or **Tools** menu.</span></span> <span data-ttu-id="90e9c-136">(Teclado: Ctrl+Alt+P)</span><span class="sxs-lookup"><span data-stu-id="90e9c-136">(Keyboard: Ctrl+Alt+P)</span></span>  
  
     <span data-ttu-id="90e9c-137">A caixa de diálogo **Processos** é exibida.</span><span class="sxs-lookup"><span data-stu-id="90e9c-137">The **Processes** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="90e9c-138">Marque a caixa de seleção **Mostrar processos de todos os usuários**.</span><span class="sxs-lookup"><span data-stu-id="90e9c-138">Select the **Show processes from all users** check box.</span></span>  
  
8.  <span data-ttu-id="90e9c-139">Na seção **Processos Disponíveis**, escolha o processo para o serviço e, em seguida, escolha **Anexar**.</span><span class="sxs-lookup"><span data-stu-id="90e9c-139">In the **Available Processes** section, choose the process for your service, and then choose **Attach**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="90e9c-140">O processo terá o mesmo nome que o arquivo executável do serviço.</span><span class="sxs-lookup"><span data-stu-id="90e9c-140">The process will have the same name as the executable file for your service.</span></span>  
  
     <span data-ttu-id="90e9c-141">A caixa de diálogo **Anexar ao Processo** é exibida.</span><span class="sxs-lookup"><span data-stu-id="90e9c-141">The **Attach to Process** dialog box appears.</span></span>  
  
9. <span data-ttu-id="90e9c-142">Escolha as opções apropriadas e, em seguida, clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="90e9c-142">Choose the appropriate options, and then choose **OK** to close the dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="90e9c-143">Agora você está no modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="90e9c-143">You are now in debug mode.</span></span>  
  
10. <span data-ttu-id="90e9c-144">Defina os pontos de interrupção que você deseja usar em seu código.</span><span class="sxs-lookup"><span data-stu-id="90e9c-144">Set any breakpoints you want to use in your code.</span></span>  
  
11. <span data-ttu-id="90e9c-145">Acesse o Gerenciador de Controle de Serviços e manuseie seu serviço, enviando comando de parar, pausar e continuar para atingir seus pontos de interrupção.</span><span class="sxs-lookup"><span data-stu-id="90e9c-145">Access the Services Control Manager and manipulate your service, sending stop, pause, and continue commands to hit your breakpoints.</span></span> <span data-ttu-id="90e9c-146">Para obter mais informações de como executar o Gerenciador de Controle de Serviços, confira [Como iniciar serviços](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="90e9c-146">For more information about running the Services Control Manager, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span> <span data-ttu-id="90e9c-147">Além disso, confira [Solução de problemas: depurando Serviços Windows](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="90e9c-147">Also, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
## <a name="debugging-tips-for-windows-services"></a><span data-ttu-id="90e9c-148">Dicas de depuração para serviços Windows</span><span class="sxs-lookup"><span data-stu-id="90e9c-148">Debugging Tips for Windows Services</span></span>  
 <span data-ttu-id="90e9c-149">Anexar ao processo do serviço permite depurar a maior parte, mas não todo, do código para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="90e9c-149">Attaching to the service's process allows you to debug most, but not all, the code for that service.</span></span> <span data-ttu-id="90e9c-150">Por exemplo, como o serviço já foi iniciado, você não pode depurar o código no serviço do método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ou o código no método `Main` que é usado para carregar o serviço dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="90e9c-150">For example, because the service has already been started, you cannot debug the code in the service's <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method or the code in the `Main` method that is used to load the service this way.</span></span> <span data-ttu-id="90e9c-151">Uma maneira de contornar essa limitação é criar um segundo serviço temporário no seu aplicativo de serviço que existe somente para ajudar na depuração.</span><span class="sxs-lookup"><span data-stu-id="90e9c-151">One way to work around this limitation is to create a temporary second service in your service application that exists only to aid in debugging.</span></span> <span data-ttu-id="90e9c-152">Você pode instalar os dois serviços e, em seguida, iniciar o serviço fictício para carregar o processo do serviço.</span><span class="sxs-lookup"><span data-stu-id="90e9c-152">You can install both services, and then start this dummy service to load the service process.</span></span> <span data-ttu-id="90e9c-153">Depois que o serviço temporário começar o processo, você poderá usar o menu **Depurar** do Visual Studio para anexar ao processo do serviço.</span><span class="sxs-lookup"><span data-stu-id="90e9c-153">Once the temporary service has started the process, you can use the **Debug** menu in Visual Studio to attach to the service process.</span></span>  
  
 <span data-ttu-id="90e9c-154">Tente adicionar chamadas para o método <xref:System.Threading.Thread.Sleep%2A> para atrasar a ação até que você possa anexar o processo.</span><span class="sxs-lookup"><span data-stu-id="90e9c-154">Try adding calls to the <xref:System.Threading.Thread.Sleep%2A> method to delay action until you’re able to attach to the process.</span></span>  
  
 <span data-ttu-id="90e9c-155">Tente alterar o programa para um aplicativo de console regular.</span><span class="sxs-lookup"><span data-stu-id="90e9c-155">Try changing the program to a regular console application.</span></span> <span data-ttu-id="90e9c-156">Para fazer isso, reescreva o método `Main` da seguinte maneira para que ele possa ser executado como um serviço Windows e como um aplicativo de console, dependendo de como for iniciado.</span><span class="sxs-lookup"><span data-stu-id="90e9c-156">To do this, rewrite the `Main` method as follows so it can run both as a Windows Service and as a console application, depending on how it's started.</span></span>  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a><span data-ttu-id="90e9c-157">Como executar um serviço Windows como um aplicativo do console</span><span class="sxs-lookup"><span data-stu-id="90e9c-157">How to: Run a Windows Service as a console application</span></span>  
  
1.  <span data-ttu-id="90e9c-158">Adicione um método para o serviço que executa os métodos <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e <xref:System.ServiceProcess.ServiceBase.OnStop%2A>:</span><span class="sxs-lookup"><span data-stu-id="90e9c-158">Add a method to your service that runs the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods:</span></span>  
  
    ```csharp  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2.  <span data-ttu-id="90e9c-159">Reescreva o método `Main` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="90e9c-159">Rewrite the `Main` method as follows:</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        if (Environment.UserInteractive)  
        {  
            MyNewService service1 = new MyNewService(args);  
            service1.TestStartupAndStop(args);  
        }  
        else  
        {  
            // Put the body of your old Main method here.  
        }  
    }
    ```  
  
3.  <span data-ttu-id="90e9c-160">Na guia **Aplicativo** das propriedades do projeto, defina o **Tipo de saída** para **Aplicativo de Console**.</span><span class="sxs-lookup"><span data-stu-id="90e9c-160">In the **Application** tab of the project's properties, set the **Output type** to **Console Application**.</span></span>  
  
4.  <span data-ttu-id="90e9c-161">Escolha **Iniciar Depuração** (F5).</span><span class="sxs-lookup"><span data-stu-id="90e9c-161">Choose **Start Debugging** (F5).</span></span>  
  
5.  <span data-ttu-id="90e9c-162">Para executar novamente o programa como um serviço Windows, instale-o e inicie-o como de costume para um serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="90e9c-162">To run the program as a Windows Service again, install it and start it as usual for a Windows Service.</span></span> <span data-ttu-id="90e9c-163">Não é necessário reverter essas alterações.</span><span class="sxs-lookup"><span data-stu-id="90e9c-163">It's not necessary to reverse these changes.</span></span>  
  
 <span data-ttu-id="90e9c-164">Em alguns casos, como quando você deseja depurar um problema ocorre apenas na inicialização do sistema, é necessário usar o depurador do Windows.</span><span class="sxs-lookup"><span data-stu-id="90e9c-164">In some cases, such as when you want to debug an issue that occurs only on system startup, you have to use the Windows debugger.</span></span> <span data-ttu-id="90e9c-165">Instale as [Ferramentas de Depuração para Windows](https://msdn.microsoft.com/windows/hardware/hh852365) e confira [Como depurar os Serviços Windows](https://support.microsoft.com/kb/824344).</span><span class="sxs-lookup"><span data-stu-id="90e9c-165">Install [Debugging Tools for Windows](https://msdn.microsoft.com/windows/hardware/hh852365) and see [How to debug Windows Services](https://support.microsoft.com/kb/824344).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90e9c-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90e9c-166">See Also</span></span>  
 [<span data-ttu-id="90e9c-167">Introdução aos Aplicativos de Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="90e9c-167">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="90e9c-168">Como instalar e desinstalar serviços</span><span class="sxs-lookup"><span data-stu-id="90e9c-168">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [<span data-ttu-id="90e9c-169">Como iniciar serviços</span><span class="sxs-lookup"><span data-stu-id="90e9c-169">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)  
 [<span data-ttu-id="90e9c-170">Depurando um serviço</span><span class="sxs-lookup"><span data-stu-id="90e9c-170">Debugging a Service</span></span>](/windows/desktop/Services/debugging-a-service)
