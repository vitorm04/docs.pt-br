---
title: 'Como: Depurar aplicativos do serviço Windows'
description: Entenda como depurar aplicativos de serviço do Windows, que não são tão simples de depurar quanto outros tipos de aplicativos do Visual Studio.
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows NT services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
author: ghogen
ms.openlocfilehash: fb58f2ff4f480347f0f233ecd9a619cf287cfdfd
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925755"
---
# <a name="how-to-debug-windows-service-applications"></a><span data-ttu-id="66cbf-103">Como: Depurar aplicativos do serviço Windows</span><span class="sxs-lookup"><span data-stu-id="66cbf-103">How to: Debug Windows Service Applications</span></span>
<span data-ttu-id="66cbf-104">Um serviço deve ser executado de dentro do contexto do Gerenciador de Controle de Serviços, em vez de dentro do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="66cbf-104">A service must be run from within the context of the Services Control Manager rather than from within Visual Studio.</span></span> <span data-ttu-id="66cbf-105">Por esse motivo, depurar um serviço não é tão simples como depurar outros tipos de aplicativos do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="66cbf-105">For this reason, debugging a service is not as straightforward as debugging other Visual Studio application types.</span></span> <span data-ttu-id="66cbf-106">Para depurar um serviço, você deve iniciar o serviço e, em seguida, anexar um depurador ao processo no qual ele está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="66cbf-106">To debug a service, you must start the service and then attach a debugger to the process in which it is running.</span></span> <span data-ttu-id="66cbf-107">Em seguida, você pode depurar seu aplicativo usando todas as funcionalidades de depuração padrão do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="66cbf-107">You can then debug your application by using all of the standard debugging functionality of Visual Studio.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="66cbf-108">Você não deve anexá-lo a um processo, a menos que você saiba qual é o processo e entenda as consequências da anexação, possivelmente eliminando esse processo.</span><span class="sxs-lookup"><span data-stu-id="66cbf-108">You should not attach to a process unless you know what the process is and understand the consequences of attaching to and possibly killing that process.</span></span> <span data-ttu-id="66cbf-109">Por exemplo, se você anexá-lo ao processo WinLogon e interromper a depuração, o sistema será interrompido porque ele não pode operar sem o WinLogon.</span><span class="sxs-lookup"><span data-stu-id="66cbf-109">For example, if you attach to the WinLogon process and then stop debugging, the system will halt because it can’t operate without WinLogon.</span></span>  
  
 <span data-ttu-id="66cbf-110">Você pode anexar o depurador somente a um serviço em execução.</span><span class="sxs-lookup"><span data-stu-id="66cbf-110">You can attach the debugger only to a running service.</span></span> <span data-ttu-id="66cbf-111">O processo de anexação interrompe o funcionamento atual do seu serviço. Na verdade, ele não para ou pausa o processamento do serviço.</span><span class="sxs-lookup"><span data-stu-id="66cbf-111">The attachment process interrupts the current functioning of your service; it doesn’t actually stop or pause the service's processing.</span></span> <span data-ttu-id="66cbf-112">Ou seja, se o serviço está sendo executado quando você inicia a depuração, ele ainda está tecnicamente num estado inicial conforme você depura, mas seu processamento foi suspenso.</span><span class="sxs-lookup"><span data-stu-id="66cbf-112">That is, if your service is running when you begin debugging, it is still technically in the Started state as you debug it, but its processing has been suspended.</span></span>  
  
 <span data-ttu-id="66cbf-113">Depois de anexá-lo ao processo, você pode definir pontos de interrupção e usá-los para depurar seu código.</span><span class="sxs-lookup"><span data-stu-id="66cbf-113">After attaching to the process, you can set breakpoints and use these to debug your code.</span></span> <span data-ttu-id="66cbf-114">Depois que sair da caixa de diálogo usada para anexá-lo ao processo, você estará efetivamente em modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="66cbf-114">Once you exit the dialog box you use to attach to the process, you are effectively in debug mode.</span></span> <span data-ttu-id="66cbf-115">Você pode usar o Gerenciador de Controle de Serviços para iniciar, parar, pausar e continuar seu serviço, alcançando, assim, os pontos de interrupção que você definiu.</span><span class="sxs-lookup"><span data-stu-id="66cbf-115">You can use the Services Control Manager to start, stop, pause and continue your service, thus hitting the breakpoints you've set.</span></span> <span data-ttu-id="66cbf-116">Posteriormente, você pode remover esse serviço fictício depois de depuração ser concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="66cbf-116">You can later remove this dummy service after debugging is successful.</span></span>  
  
 <span data-ttu-id="66cbf-117">Este artigo aborda a depuração de um serviço que está em execução no computador local, mas você também pode depurar serviços Windows que executados em um computador remoto.</span><span class="sxs-lookup"><span data-stu-id="66cbf-117">This article covers debugging a service that's running on the local computer, but you can also debug Windows Services that are running on a remote computer.</span></span> <span data-ttu-id="66cbf-118">Confira [Depuração remota](/visualstudio/debugger/debug-installed-app-package).</span><span class="sxs-lookup"><span data-stu-id="66cbf-118">See [Remote Debugging](/visualstudio/debugger/debug-installed-app-package).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66cbf-119">Depurar o método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> pode ser difícil porque o Gerenciador de controle de Serviços impõe um limite de 30 segundos em todas as tentativas de iniciar um serviço.</span><span class="sxs-lookup"><span data-stu-id="66cbf-119">Debugging the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method can be difficult because the Services Control Manager imposes a 30-second limit on all attempts to start a service.</span></span> <span data-ttu-id="66cbf-120">Para obter mais informações, confira [Solução de problemas: depuração de Serviços Windows](troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="66cbf-120">For more information, see [Troubleshooting: Debugging Windows Services](troubleshooting-debugging-windows-services.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="66cbf-121">Para obter informações significativas para depuração, o depurador do Visual Studio deve localizar os arquivos de símbolo para os binários que estão sendo depurados.</span><span class="sxs-lookup"><span data-stu-id="66cbf-121">To get meaningful information for debugging, the Visual Studio debugger needs to find symbol files for the binaries that are being debugged.</span></span> <span data-ttu-id="66cbf-122">Se você estiver depurando um serviço que você criou no Visual Studio, os arquivos de símbolo (arquivos .pdb) estarão na mesma pasta que o executável ou biblioteca, e o depurador os carregará automaticamente.</span><span class="sxs-lookup"><span data-stu-id="66cbf-122">If you are debugging a service that you built in Visual Studio, the symbol files (.pdb files) are in the same folder as the executable or library, and the debugger loads them automatically.</span></span> <span data-ttu-id="66cbf-123">Se você estiver depurando um serviço que não criou, deve primeiro localizar símbolos para o serviço e certificar-se de que eles podem ser encontrados pelo depurador.</span><span class="sxs-lookup"><span data-stu-id="66cbf-123">If you are debugging a service that you didn't build, you should first find symbols for the service and make sure they can be found by the debugger.</span></span> <span data-ttu-id="66cbf-124">Confira [Especificar arquivos de símbolo (.pdb) e de origem no Depurador do Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span><span class="sxs-lookup"><span data-stu-id="66cbf-124">See [Specify Symbol (.pdb) and Source Files in the Visual Studio Debugger](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span></span> <span data-ttu-id="66cbf-125">Se você estiver depurando um processo do sistema ou se desejar ter símbolos para chamadas do sistema em seus serviços, você deve adicionar os Servidores de Símbolo Microsoft.</span><span class="sxs-lookup"><span data-stu-id="66cbf-125">If you're debugging a system process or want to have symbols for system calls in your services, you should add the Microsoft Symbol Servers.</span></span> <span data-ttu-id="66cbf-126">Confira [Depurando símbolos](/windows/desktop/DxTechArts/debugging-with-symbols).</span><span class="sxs-lookup"><span data-stu-id="66cbf-126">See [Debugging Symbols](/windows/desktop/DxTechArts/debugging-with-symbols).</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="66cbf-127">Para depurar um serviço</span><span class="sxs-lookup"><span data-stu-id="66cbf-127">To debug a service</span></span>  
  
1. <span data-ttu-id="66cbf-128">Crie seu serviço na configuração de depuração.</span><span class="sxs-lookup"><span data-stu-id="66cbf-128">Build your service in the Debug configuration.</span></span>  
  
2. <span data-ttu-id="66cbf-129">Instalar o serviço.</span><span class="sxs-lookup"><span data-stu-id="66cbf-129">Install your service.</span></span> <span data-ttu-id="66cbf-130">Para obter mais informações, confira [Como instalar e desinstalar serviços](how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="66cbf-130">For more information, see [How to: Install and Uninstall Services](how-to-install-and-uninstall-services.md).</span></span>  
  
3. <span data-ttu-id="66cbf-131">Inicie o serviço, usando o **Gerenciador de Controle de Serviços**, o **Gerenciador de Servidores** ou o código.</span><span class="sxs-lookup"><span data-stu-id="66cbf-131">Start your service, either from **Services Control Manager**, **Server Explorer**, or from code.</span></span> <span data-ttu-id="66cbf-132">Para obter mais informações, confira [Como iniciar serviços](how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="66cbf-132">For more information, see [How to: Start Services](how-to-start-services.md).</span></span>  
  
4. <span data-ttu-id="66cbf-133">Inicie o Visual Studio com credenciais administrativas para que você possa se conectar aos processos do sistema.</span><span class="sxs-lookup"><span data-stu-id="66cbf-133">Start Visual Studio with administrative credentials so you can attach to system processes.</span></span>  
  
5. <span data-ttu-id="66cbf-134">(Opcional) Na barra de menus do Visual Studio, escolha **Ferramentas**, **Opções**.</span><span class="sxs-lookup"><span data-stu-id="66cbf-134">(Optional) On the Visual Studio menu bar, choose **Tools**, **Options**.</span></span> <span data-ttu-id="66cbf-135">Na caixa de diálogo **Opções**, escolha **Depuração**, **Símbolos**, marque a caixa de seleção **Servidores de Símbolos da Microsoft** e, em seguida, clique no botão **OK**.</span><span class="sxs-lookup"><span data-stu-id="66cbf-135">In the **Options** dialog box, choose **Debugging**, **Symbols**, select the **Microsoft Symbol Servers** check box, and then choose the **OK** button.</span></span>  
  
6. <span data-ttu-id="66cbf-136">Na barra de menus, escolha **Anexar ao Processo** no menu **Depurar** ou **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="66cbf-136">On the menu bar, choose **Attach to Process** from the **Debug** or **Tools** menu.</span></span> <span data-ttu-id="66cbf-137">(Teclado: Ctrl+Alt+P)</span><span class="sxs-lookup"><span data-stu-id="66cbf-137">(Keyboard: Ctrl+Alt+P)</span></span>  
  
     <span data-ttu-id="66cbf-138">A caixa de diálogo **Processos** é exibida.</span><span class="sxs-lookup"><span data-stu-id="66cbf-138">The **Processes** dialog box appears.</span></span>  
  
7. <span data-ttu-id="66cbf-139">Marque a caixa de seleção **Mostrar processos de todos os usuários**.</span><span class="sxs-lookup"><span data-stu-id="66cbf-139">Select the **Show processes from all users** check box.</span></span>  
  
8. <span data-ttu-id="66cbf-140">Na seção **Processos Disponíveis**, escolha o processo para o serviço e, em seguida, escolha **Anexar**.</span><span class="sxs-lookup"><span data-stu-id="66cbf-140">In the **Available Processes** section, choose the process for your service, and then choose **Attach**.</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="66cbf-141">O processo terá o mesmo nome que o arquivo executável do serviço.</span><span class="sxs-lookup"><span data-stu-id="66cbf-141">The process will have the same name as the executable file for your service.</span></span>  
  
     <span data-ttu-id="66cbf-142">A caixa de diálogo **Anexar ao Processo** é exibida.</span><span class="sxs-lookup"><span data-stu-id="66cbf-142">The **Attach to Process** dialog box appears.</span></span>  
  
9. <span data-ttu-id="66cbf-143">Escolha as opções apropriadas e, em seguida, clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="66cbf-143">Choose the appropriate options, and then choose **OK** to close the dialog box.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="66cbf-144">Agora você está no modo de depuração.</span><span class="sxs-lookup"><span data-stu-id="66cbf-144">You are now in debug mode.</span></span>  
  
10. <span data-ttu-id="66cbf-145">Defina os pontos de interrupção que você deseja usar em seu código.</span><span class="sxs-lookup"><span data-stu-id="66cbf-145">Set any breakpoints you want to use in your code.</span></span>  
  
11. <span data-ttu-id="66cbf-146">Acesse o Gerenciador de Controle de Serviços e manuseie seu serviço, enviando comando de parar, pausar e continuar para atingir seus pontos de interrupção.</span><span class="sxs-lookup"><span data-stu-id="66cbf-146">Access the Services Control Manager and manipulate your service, sending stop, pause, and continue commands to hit your breakpoints.</span></span> <span data-ttu-id="66cbf-147">Para obter mais informações de como executar o Gerenciador de Controle de Serviços, confira [Como iniciar serviços](how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="66cbf-147">For more information about running the Services Control Manager, see [How to: Start Services](how-to-start-services.md).</span></span> <span data-ttu-id="66cbf-148">Além disso, confira [Solução de problemas: depurando Serviços Windows](troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="66cbf-148">Also, see [Troubleshooting: Debugging Windows Services](troubleshooting-debugging-windows-services.md).</span></span>  
  
## <a name="debugging-tips-for-windows-services"></a><span data-ttu-id="66cbf-149">Dicas de depuração para serviços Windows</span><span class="sxs-lookup"><span data-stu-id="66cbf-149">Debugging Tips for Windows Services</span></span>  
 <span data-ttu-id="66cbf-150">Anexar ao processo do serviço permite depurar a maior parte, mas não todo, do código para esse serviço.</span><span class="sxs-lookup"><span data-stu-id="66cbf-150">Attaching to the service's process allows you to debug most, but not all, the code for that service.</span></span> <span data-ttu-id="66cbf-151">Por exemplo, como o serviço já foi iniciado, você não pode depurar o código no serviço do método <xref:System.ServiceProcess.ServiceBase.OnStart%2A> ou o código no método `Main` que é usado para carregar o serviço dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="66cbf-151">For example, because the service has already been started, you cannot debug the code in the service's <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method or the code in the `Main` method that is used to load the service this way.</span></span> <span data-ttu-id="66cbf-152">Uma maneira de contornar essa limitação é criar um segundo serviço temporário no seu aplicativo de serviço que existe somente para ajudar na depuração.</span><span class="sxs-lookup"><span data-stu-id="66cbf-152">One way to work around this limitation is to create a temporary second service in your service application that exists only to aid in debugging.</span></span> <span data-ttu-id="66cbf-153">Você pode instalar os dois serviços e, em seguida, iniciar o serviço fictício para carregar o processo do serviço.</span><span class="sxs-lookup"><span data-stu-id="66cbf-153">You can install both services, and then start this dummy service to load the service process.</span></span> <span data-ttu-id="66cbf-154">Depois que o serviço temporário começar o processo, você poderá usar o menu **Depurar** do Visual Studio para anexar ao processo do serviço.</span><span class="sxs-lookup"><span data-stu-id="66cbf-154">Once the temporary service has started the process, you can use the **Debug** menu in Visual Studio to attach to the service process.</span></span>  
  
 <span data-ttu-id="66cbf-155">Tente adicionar chamadas para o método <xref:System.Threading.Thread.Sleep%2A> para atrasar a ação até que você possa anexar o processo.</span><span class="sxs-lookup"><span data-stu-id="66cbf-155">Try adding calls to the <xref:System.Threading.Thread.Sleep%2A> method to delay action until you’re able to attach to the process.</span></span>  
  
 <span data-ttu-id="66cbf-156">Tente alterar o programa para um aplicativo de console regular.</span><span class="sxs-lookup"><span data-stu-id="66cbf-156">Try changing the program to a regular console application.</span></span> <span data-ttu-id="66cbf-157">Para fazer isso, reescreva o método `Main` da seguinte maneira para que ele possa ser executado como um serviço Windows e como um aplicativo de console, dependendo de como for iniciado.</span><span class="sxs-lookup"><span data-stu-id="66cbf-157">To do this, rewrite the `Main` method as follows so it can run both as a Windows Service and as a console application, depending on how it's started.</span></span>  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a><span data-ttu-id="66cbf-158">Como executar um serviço Windows como um aplicativo do console</span><span class="sxs-lookup"><span data-stu-id="66cbf-158">How to: Run a Windows Service as a console application</span></span>  
  
1. <span data-ttu-id="66cbf-159">Adicione um método para o serviço que executa os métodos <xref:System.ServiceProcess.ServiceBase.OnStart%2A> e <xref:System.ServiceProcess.ServiceBase.OnStop%2A>:</span><span class="sxs-lookup"><span data-stu-id="66cbf-159">Add a method to your service that runs the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods:</span></span>  
  
    ```csharp  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2. <span data-ttu-id="66cbf-160">Reescreva o método `Main` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="66cbf-160">Rewrite the `Main` method as follows:</span></span>  
  
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
  
3. <span data-ttu-id="66cbf-161">Na guia **Aplicativo** das propriedades do projeto, defina o **Tipo de saída** para **Aplicativo de Console**.</span><span class="sxs-lookup"><span data-stu-id="66cbf-161">In the **Application** tab of the project's properties, set the **Output type** to **Console Application**.</span></span>  
  
4. <span data-ttu-id="66cbf-162">Escolha **Iniciar Depuração** (F5).</span><span class="sxs-lookup"><span data-stu-id="66cbf-162">Choose **Start Debugging** (F5).</span></span>  
  
5. <span data-ttu-id="66cbf-163">Para executar novamente o programa como um serviço Windows, instale-o e inicie-o como de costume para um serviço Windows.</span><span class="sxs-lookup"><span data-stu-id="66cbf-163">To run the program as a Windows Service again, install it and start it as usual for a Windows Service.</span></span> <span data-ttu-id="66cbf-164">Não é necessário reverter essas alterações.</span><span class="sxs-lookup"><span data-stu-id="66cbf-164">It's not necessary to reverse these changes.</span></span>  
  
 <span data-ttu-id="66cbf-165">Em alguns casos, como quando você deseja depurar um problema ocorre apenas na inicialização do sistema, é necessário usar o depurador do Windows.</span><span class="sxs-lookup"><span data-stu-id="66cbf-165">In some cases, such as when you want to debug an issue that occurs only on system startup, you have to use the Windows debugger.</span></span> <span data-ttu-id="66cbf-166">[Baixe o Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk) e consulte [Como depurar serviços Windows](https://support.microsoft.com/kb/824344).</span><span class="sxs-lookup"><span data-stu-id="66cbf-166">[Download the Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk) and see [How to debug Windows Services](https://support.microsoft.com/kb/824344).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66cbf-167">Veja também</span><span class="sxs-lookup"><span data-stu-id="66cbf-167">See also</span></span>

- [<span data-ttu-id="66cbf-168">Introdução a aplicativos do Serviço Windows</span><span class="sxs-lookup"><span data-stu-id="66cbf-168">Introduction to Windows Service Applications</span></span>](introduction-to-windows-service-applications.md)
- [<span data-ttu-id="66cbf-169">Como: instalar e desinstalar serviços</span><span class="sxs-lookup"><span data-stu-id="66cbf-169">How to: Install and Uninstall Services</span></span>](how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="66cbf-170">Como: Iniciar serviços</span><span class="sxs-lookup"><span data-stu-id="66cbf-170">How to: Start Services</span></span>](how-to-start-services.md)
- [<span data-ttu-id="66cbf-171">Depurar um serviço</span><span class="sxs-lookup"><span data-stu-id="66cbf-171">Debugging a Service</span></span>](/windows/desktop/Services/debugging-a-service)
