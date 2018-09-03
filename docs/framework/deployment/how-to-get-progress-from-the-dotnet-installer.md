---
title: Como acompanhar o progresso do Instalador do .NET Framework 4.5
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- progress information, .NET Framework installer
- .NET Framework, installing
ms.assetid: 0a1a3ba3-7e46-4df2-afd3-f3a8237e1c4f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c27bdb75ef9950d0b2b32f742b38e141cf4981b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43472040"
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a><span data-ttu-id="74c0d-102">Como acompanhar o progresso do Instalador do .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="74c0d-102">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>
<span data-ttu-id="74c0d-103">O [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] é um tempo de execução redistribuível.</span><span class="sxs-lookup"><span data-stu-id="74c0d-103">The [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is a redistributable runtime.</span></span> <span data-ttu-id="74c0d-104">Se você desenvolver aplicativos para esta versão do .NET Framework, poderá incluir (encadear) a instalação de [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] como uma parte de pré-requisito da instalação do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74c0d-104">If you develop apps for this version of the .NET Framework, you can include (chain) [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup as a prerequisite part of your app's setup.</span></span> <span data-ttu-id="74c0d-105">Para apresentar uma experiência de instalação personalizada ou unificada, talvez você queira iniciar silenciosamente a instalação de [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] e acompanhar seu progresso enquanto mostra o progresso da instalação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74c0d-105">To present a customized or unified setup experience, you may want to silently launch [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup and track its progress while showing your app's setup progress.</span></span> <span data-ttu-id="74c0d-106">Para habilitar o acompanhamento silencioso, a instalação do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] (que pode ser inspecionada) define um protocolo usando uma MMIO (E/S mapeada em memória) para se comunicar com a instalação (o inspetor ou encadeador).</span><span class="sxs-lookup"><span data-stu-id="74c0d-106">To enable silent tracking, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup (which can be watched) defines a protocol by using a memory-mapped I/O (MMIO) segment to communicate with your setup (the watcher or chainer).</span></span> <span data-ttu-id="74c0d-107">Esse protocolo define uma maneira para um encadeador obter informações sobre o progresso, obter resultados detalhados, responder às mensagens e cancelar a instalação do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="74c0d-107">This protocol defines a way for a chainer to obtain progress information, get detailed results, respond to messages, and cancel the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup.</span></span>  
  
-   <span data-ttu-id="74c0d-108">**Invocação**.</span><span class="sxs-lookup"><span data-stu-id="74c0d-108">**Invocation** .</span></span>  <span data-ttu-id="74c0d-109">Para chamar a instalação do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] e receber informações sobre o progresso da seção MMIO, seu programa de instalação deve fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="74c0d-109">To call [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup and receive progress information from the MMIO section, your setup program must do the following:</span></span>  
  
    1.  <span data-ttu-id="74c0d-110">Chamar o programa redistribuível [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="74c0d-110">Call the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]redistributable program:</span></span>  
  
        ```  
        dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name  
        ```  
  
         <span data-ttu-id="74c0d-111">em que *nome da seção* é qualquer nome que você deseja usar para identificar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74c0d-111">where *section name* is any name you want to use to identify your app.</span></span> <span data-ttu-id="74c0d-112">A instalação do .NET Framework lê e grava na seção MMIO assincronamente, portanto, talvez seja conveniente usar eventos e mensagens durante esse período.</span><span class="sxs-lookup"><span data-stu-id="74c0d-112">.NET Framework setup reads and writes to the MMIO section asynchronously, so you might find it convenient to use events and messages during that time.</span></span> <span data-ttu-id="74c0d-113">No exemplo, o processo de instalação do .NET Framework é criado por um construtor que aloca a seção MMIO (`TheSectionName`) e define um evento (`TheEventName`):</span><span class="sxs-lookup"><span data-stu-id="74c0d-113">In the example, the .NET Framework setup process is created by a constructor that both allocates the MMIO section (`TheSectionName`) and defines an event (`TheEventName`):</span></span>  
  
        ```  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")  
        ```  
  
         <span data-ttu-id="74c0d-114">Substitua esses nomes por nomes que são exclusivos para seu programa de instalação.</span><span class="sxs-lookup"><span data-stu-id="74c0d-114">Please replace those names with names that are unique to your setup program.</span></span>  
  
    2.  <span data-ttu-id="74c0d-115">Leia a seção MMIO.</span><span class="sxs-lookup"><span data-stu-id="74c0d-115">Read from the MMIO section.</span></span> <span data-ttu-id="74c0d-116">No [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], as operações de download e instalação são simultâneas: uma parte do .NET Framework pode ser instalada enquanto outra parte está baixando.</span><span class="sxs-lookup"><span data-stu-id="74c0d-116">In the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], the download and installation operations are simultaneous: One part of the .NET Framework might be installing while another part is downloading.</span></span> <span data-ttu-id="74c0d-117">Como resultado, o progresso é enviado novamente (isto é, gravado) para a seção MMIO como dois números (`m_downloadSoFar` e `m_installSoFar`) que aumentam de 0 a 255.</span><span class="sxs-lookup"><span data-stu-id="74c0d-117">As a result, progress is sent back (that is, written) to the MMIO section as two numbers (`m_downloadSoFar` and `m_installSoFar`) that increase from 0 to 255.</span></span> <span data-ttu-id="74c0d-118">Quando 255 é gravado e o .NET Framework sai, a instalação está concluída.</span><span class="sxs-lookup"><span data-stu-id="74c0d-118">When 255 is written and the .NET Framework exits, the installation is complete.</span></span>  
  
-   <span data-ttu-id="74c0d-119">**Códigos de saída**.</span><span class="sxs-lookup"><span data-stu-id="74c0d-119">**Exit codes**.</span></span> <span data-ttu-id="74c0d-120">Os códigos de saída a seguir do comando para chamar o programa redistribuível [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] indicam se a instalação teve êxito ou falhou:</span><span class="sxs-lookup"><span data-stu-id="74c0d-120">The following exit codes from the command to call the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable program indicate whether setup has succeeded or failed:</span></span>  
  
    -   <span data-ttu-id="74c0d-121">0 – Instalação concluída com êxito.</span><span class="sxs-lookup"><span data-stu-id="74c0d-121">0 - Setup completed successfully.</span></span>  
  
    -   <span data-ttu-id="74c0d-122">3010 – Instalação concluída com êxito. É necessário reiniciar o sistema.</span><span class="sxs-lookup"><span data-stu-id="74c0d-122">3010 – Setup completed successfully; a system restart is required.</span></span>  
  
    -   <span data-ttu-id="74c0d-123">1602 – A instalação foi cancelada.</span><span class="sxs-lookup"><span data-stu-id="74c0d-123">1602 – Setup has been canceled.</span></span>  
  
    -   <span data-ttu-id="74c0d-124">Todos os outros códigos – A instalação encontrou erros. Examine os arquivos de log criados em %temp% para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="74c0d-124">All other codes - Setup encountered errors; examine the log files created in %temp% for details.</span></span>  
  
-   <span data-ttu-id="74c0d-125">**Cancelando a instalação**.</span><span class="sxs-lookup"><span data-stu-id="74c0d-125">**Canceling setup**.</span></span> <span data-ttu-id="74c0d-126">Você pode cancelar a instalação a qualquer momento usando o método `Abort` para definir os sinalizadores `m_downloadAbort` e `m_ installAbort` na seção MMIO.</span><span class="sxs-lookup"><span data-stu-id="74c0d-126">You can cancel setup at any time by using the `Abort` method to set the `m_downloadAbort` and `m_ installAbort` flags in the MMIO section.</span></span>  
  
## <a name="chainer-sample"></a><span data-ttu-id="74c0d-127">Exemplo de encadeador</span><span class="sxs-lookup"><span data-stu-id="74c0d-127">Chainer Sample</span></span>  
 <span data-ttu-id="74c0d-128">O exemplo de encadeador inicializa e controla silenciosamente a instalação do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] enquanto mostra o progresso.</span><span class="sxs-lookup"><span data-stu-id="74c0d-128">The Chainer sample silently launches and tracks [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup while showing progress.</span></span> <span data-ttu-id="74c0d-129">Este exemplo é semelhante ao exemplo de encadeador fornecido para o .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="74c0d-129">This sample is similar to the Chainer sample provided for the .NET Framework 4.</span></span> <span data-ttu-id="74c0d-130">No entanto, além disso, ele pode evitar reinicializações do sistema processando a caixa de mensagem para fechar os aplicativos do .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="74c0d-130">However, in addition, it can avoid system restarts by processing the message box for closing .NET Framework 4 apps.</span></span> <span data-ttu-id="74c0d-131">Para obter informações sobre essa caixa de mensagens, consulte [Redução de reinicializações do sistema durante instalações do .NET Framework 4.5](../../../docs/framework/deployment/reducing-system-restarts.md).</span><span class="sxs-lookup"><span data-stu-id="74c0d-131">For information about this message box, see [Reducing System Restarts During .NET Framework 4.5 Installations](../../../docs/framework/deployment/reducing-system-restarts.md).</span></span> <span data-ttu-id="74c0d-132">Você pode usar este exemplo com o instalador do .NET Framework 4. Nesse cenário, a mensagem simplesmente não é enviada.</span><span class="sxs-lookup"><span data-stu-id="74c0d-132">You can use this sample with the .NET Framework 4 installer; in that scenario, the message is simply not sent.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="74c0d-133">Você deve executar o exemplo como um administrador.</span><span class="sxs-lookup"><span data-stu-id="74c0d-133">You must run the example as an administrator.</span></span>  
  
 <span data-ttu-id="74c0d-134">Você pode baixar a solução completa do Visual Studio para o [.NET Framework 4.5 Chainer Sample](https://go.microsoft.com/fwlink/?LinkId=231345) na Galeria de Exemplos do MSDN.</span><span class="sxs-lookup"><span data-stu-id="74c0d-134">You can download the complete Visual Studio solution for the [.NET Framework 4.5 Chainer Sample](https://go.microsoft.com/fwlink/?LinkId=231345) from the MSDN Samples Gallery.</span></span>  
  
 <span data-ttu-id="74c0d-135">As seções a seguir descrevem os arquivos significativos neste exemplo: MMIOChainer.h, ChainingdotNet4.cpp e IProgressObserver.h.</span><span class="sxs-lookup"><span data-stu-id="74c0d-135">The following sections describe the significant files in this sample: MMIOChainer.h, ChainingdotNet4.cpp, and IProgressObserver.h.</span></span>  
  
#### <a name="mmiochainerh"></a><span data-ttu-id="74c0d-136">MMIOChainer.h</span><span class="sxs-lookup"><span data-stu-id="74c0d-136">MMIOChainer.h</span></span>  
  
-   <span data-ttu-id="74c0d-137">O arquivo MMIOChainer.h (consulte o [código completo](https://go.microsoft.com/fwlink/?LinkId=231369)) contém a definição da estrutura de dados e a classe base da qual a classe do encadeador deve ser derivada.</span><span class="sxs-lookup"><span data-stu-id="74c0d-137">The MMIOChainer.h file (see [complete code](https://go.microsoft.com/fwlink/?LinkId=231369)) contains the data structure definition and the base class from which the chainer class should be derived.</span></span> <span data-ttu-id="74c0d-138">O [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] estende a estrutura de dados MMIO para lidar com os dados que instalador do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] precisa.</span><span class="sxs-lookup"><span data-stu-id="74c0d-138">The [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] extends the MMIO data structure to handle data that the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] installer needs.</span></span> <span data-ttu-id="74c0d-139">As alterações na estrutura MMIO têm compatibilidade com versões anteriores, portanto, um encadeador do .NET Framework 4 pode funcionar com a instalação do .NET Framework 4.5 sem a necessidade de recompilação.</span><span class="sxs-lookup"><span data-stu-id="74c0d-139">The changes to the MMIO structure are backward-compatible, so a .NET Framework 4 chainer can work with .NET Framework 4.5 setup without requiring recompilation.</span></span> <span data-ttu-id="74c0d-140">No entanto, esse cenário não dá suporte ao recurso para reduzir as reinicializações do sistema.</span><span class="sxs-lookup"><span data-stu-id="74c0d-140">However, this scenario does not support the feature for reducing system restarts.</span></span>  
  
     <span data-ttu-id="74c0d-141">Um campo de versão fornece um meio de identificar as revisões do formato de mensagem e de estrutura.</span><span class="sxs-lookup"><span data-stu-id="74c0d-141">A version field provides a means of identifying revisions to the structure and message format.</span></span>  <span data-ttu-id="74c0d-142">A instalação do .NET Framework determina a versão da interface do encadeador chamando a função `VirtualQuery` para determinar o tamanho do mapeamento de arquivo.</span><span class="sxs-lookup"><span data-stu-id="74c0d-142">The .NET Framework setup determines the version of the chainer interface by calling the `VirtualQuery` function to determine the size of the file mapping.</span></span>  <span data-ttu-id="74c0d-143">Se o tamanho for grande o suficiente para acomodar o campo de versão, a instalação do .NET Framework usa o valor especificado.</span><span class="sxs-lookup"><span data-stu-id="74c0d-143">If the size is large enough to accommodate the version field, .NET Framework setup uses the specified value.</span></span> <span data-ttu-id="74c0d-144">Se o mapeamento de arquivo for muito pequeno para conter um campo de versão, que é o caso com o .NET Framework 4, o processo de instalação assume a versão 0 (4).</span><span class="sxs-lookup"><span data-stu-id="74c0d-144">If the file mapping is too small to contain a version field, which is the case with the .NET Framework 4, the setup process assumes version 0 (4).</span></span> <span data-ttu-id="74c0d-145">Se o encadeador não dá suporte à versão da mensagem que o instalador do .NET Framework deseja enviar, a instalação do .NET Framework assume uma resposta de ignorar.</span><span class="sxs-lookup"><span data-stu-id="74c0d-145">If the chainer does not support the version of the message that .NET Framework setup wants to send, .NET Framework setup assumes an ignore response.</span></span>  
  
     <span data-ttu-id="74c0d-146">A estrutura de dados MMIO é definida da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="74c0d-146">The MMIO data structure is defined as follows:</span></span>  
  
    ```cpp  
    // MMIO data structure for interprocess communication  
        struct MmioDataStructure  
        {  
            bool m_downloadFinished;               // Is download complete?  
            bool m_installFinished;                // Is installation complete?  
            bool m_downloadAbort;                  // Set to cause downloader to abort.  
            bool m_installAbort;                   // Set to cause installer to abort.  
            HRESULT m_hrDownloadFinished;          // Resulting HRESULT for download.  
            HRESULT m_hrInstallFinished;           // Resulting HRESULT for installation.  
            HRESULT m_hrInternalError;  
            WCHAR m_szCurrentItemStep[MAX_PATH];  
            unsigned char m_downloadSoFar;         // Download progress 0-255 (0-100% done).   
            unsigned char m_installSoFar;          // Installation progress 0-255 (0-100% done).  
            WCHAR m_szEventName[MAX_PATH];         // Event that chainer creates and chainee opens to sync communications.  
  
            BYTE m_version;                        // Version of the data structure, set by chainer:  
                                                   // 0x0: .NET Framework 4   
                                                   // 0x1: .NET Framework 4.5  
  
            DWORD m_messageCode;                   // Current message sent by the chainee; 0 if no message is active.  
            DWORD m_messageResponse;               // Chainer's response to current message; 0 if not yet handled.  
            DWORD m_messageDataLength;             // Length of the m_messageData field, in bytes.  
            BYTE m_messageData[1];                 // Variable-length buffer; content depends on m_messageCode.  
        };  
    ```  
  
-   <span data-ttu-id="74c0d-147">A estrutura de dados `MmioDataStructure` não deve ser usada diretamente, use a classe `MmioChainer` em vez disso para implementar o encadeador.</span><span class="sxs-lookup"><span data-stu-id="74c0d-147">The `MmioDataStructure` data structure should not be used directly; use the `MmioChainer` class instead to implement your chainer.</span></span> <span data-ttu-id="74c0d-148">Derive da classe `MmioChainer` para encadear o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistribuível.</span><span class="sxs-lookup"><span data-stu-id="74c0d-148">Derive from the `MmioChainer` class to chain the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable.</span></span>  
  
#### <a name="iprogressobserverh"></a><span data-ttu-id="74c0d-149">IProgressObserver.h</span><span class="sxs-lookup"><span data-stu-id="74c0d-149">IProgressObserver.h</span></span>  
  
-   <span data-ttu-id="74c0d-150">O arquivo IProgressObserver.h implementa um observador de progresso ([veja o código completo](https://go.microsoft.com/fwlink/?LinkId=231370)).</span><span class="sxs-lookup"><span data-stu-id="74c0d-150">The IProgressObserver.h file implements a progress observer ([see complete code](https://go.microsoft.com/fwlink/?LinkId=231370)).</span></span> <span data-ttu-id="74c0d-151">Este observador é notificado sobre o progresso do download e da instalação (especificado como um `char` sem sinal, 0 a 255, que indica 1 a 100% concluído).</span><span class="sxs-lookup"><span data-stu-id="74c0d-151">This observer gets notified of download and installation progress (specified as an unsigned `char`, 0-255, indicating 1%-100% complete).</span></span> <span data-ttu-id="74c0d-152">O observador também é notificado quando o encadeador envia uma mensagem e o observador deve enviar uma resposta.</span><span class="sxs-lookup"><span data-stu-id="74c0d-152">The observer is also notified when the chainee sends a message, and the observer should send a response.</span></span>  
  
    ```cpp  
        class IProgressObserver  
        {  
        public:  
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%  
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete    
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent  
        };  
    ```  
  
#### <a name="chainingdotnet45cpp"></a><span data-ttu-id="74c0d-153">ChainingdotNet4.5.cpp</span><span class="sxs-lookup"><span data-stu-id="74c0d-153">ChainingdotNet4.5.cpp</span></span>  
  
-   <span data-ttu-id="74c0d-154">O arquivo [ChainingdotNet4.5.cpp](https://go.microsoft.com/fwlink/?LinkId=231368) implementa a classe `Server`, que deriva da classe `MmioChainer` e substitui os métodos apropriados para exibir informações sobre o progresso.</span><span class="sxs-lookup"><span data-stu-id="74c0d-154">The [ChainingdotNet4.5.cpp](https://go.microsoft.com/fwlink/?LinkId=231368) file implements the `Server` class, which derives from the `MmioChainer` class and overrides the appropriate methods to display progress information.</span></span> <span data-ttu-id="74c0d-155">O MmioChainer cria uma seção com o nome da seção especificado e inicializa o encadeador com o nome do evento especificado.</span><span class="sxs-lookup"><span data-stu-id="74c0d-155">The MmioChainer creates a section with the specified section name and initializes the chainer with the specified event name.</span></span> <span data-ttu-id="74c0d-156">O nome do evento é salvo na estrutura de dados mapeada.</span><span class="sxs-lookup"><span data-stu-id="74c0d-156">The event name is saved in the mapped data structure.</span></span> <span data-ttu-id="74c0d-157">Você deve tornar os nomes da seção e do evento exclusivos.</span><span class="sxs-lookup"><span data-stu-id="74c0d-157">You should make the section and event names unique.</span></span> <span data-ttu-id="74c0d-158">A classe `Server` no código a seguir inicia o programa de instalação especificado, monitora o progresso e retorna um código de saída.</span><span class="sxs-lookup"><span data-stu-id="74c0d-158">The `Server` class in the following code launches the specified setup program, monitors its progress, and returns an exit code.</span></span>  
  
    ```cpp  
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver  
    {  
    public:  
        …………….  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names  
        {}  
    ```  
  
     <span data-ttu-id="74c0d-159">A instalação é iniciada no método Main.</span><span class="sxs-lookup"><span data-stu-id="74c0d-159">The installation is started in the Main method.</span></span>  
  
    ```cpp  
    // Main entry point for program  
    int __cdecl main(int argc, _In_count_(argc) char **_argv)  
    {  
        int result = 0;  
        CString args;  
        if (argc > 1)  
        {  
            args = CString(_argv[1]);  
        }  
  
        if (IsNetFx4Present(NETFX45_RC_REVISION))  
        {  
            printf(".NET Framework 4.5 is already installed");  
        }  
        else  
        {  
            result = Server().Launch(args);  
        }  
  
        return result;  
    }  
    ```  
  
-   <span data-ttu-id="74c0d-160">Antes de iniciar a instalação, o encadeador verifica se o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] já está instalado chamando `IsNetFx4Present`:</span><span class="sxs-lookup"><span data-stu-id="74c0d-160">Before launching the installation, the chainer checks to see if the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is already installed by calling `IsNetFx4Present`:</span></span>  
  
    ```cpp  
    ///  Checks for presence of the .NET Framework 4.  
    ///    A value of 0 for dwMinimumRelease indicates a check for the .NET Framework 4 full  
    ///    Any other value indicates a check for a specific compatible release of the .NET Framework 4.  
    #define NETFX40_FULL_REVISION 0  
    // TODO: Replace with released revision number  
    #define NETFX45_RC_REVISION MAKELONG(50309, 5)   // .NET Framework 4.5   
    bool IsNetFx4Present(DWORD dwMinimumRelease)  
    {  
        DWORD dwError = ERROR_SUCCESS;  
        HKEY hKey = NULL;  
        DWORD dwData = 0;  
        DWORD dwType = 0;  
        DWORD dwSize = sizeof(dwData);  
  
        dwError = ::RegOpenKeyExW(HKEY_LOCAL_MACHINE, L"SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full", 0, KEY_READ, &hKey);  
        if (ERROR_SUCCESS == dwError)  
        {  
            dwError = ::RegQueryValueExW(hKey, L"Release", 0, &dwType, (LPBYTE)&dwData, &dwSize);  
  
            if ((ERROR_SUCCESS == dwError) && (REG_DWORD != dwType))  
            {  
                dwError = ERROR_INVALID_DATA;  
            }  
            else if (ERROR_FILE_NOT_FOUND == dwError)  
            {  
                // Release value was not found, let's check for 4.0.  
                dwError = ::RegQueryValueExW(hKey, L"Install", 0, &dwType, (LPBYTE)&dwData, &dwSize);  
  
                // Install = (REG_DWORD)1;  
                if ((ERROR_SUCCESS == dwError) && (REG_DWORD == dwType) && (dwData == 1))  
                {  
                    // treat 4.0 as Release = 0  
                    dwData = 0;  
                }  
                else  
                {  
                    dwError = ERROR_INVALID_DATA;  
                }  
            }  
        }  
  
        if (hKey != NULL)  
        {  
            ::RegCloseKey(hKey);  
        }  
  
        return ((ERROR_SUCCESS == dwError) && (dwData >= dwMinimumRelease));  
    }  
    ```  
  
-   <span data-ttu-id="74c0d-161">Você pode alterar o caminho do executável (Setup.exe no exemplo) no método `Launch` para apontar para o local correto ou personalizar o código para determinar o local.</span><span class="sxs-lookup"><span data-stu-id="74c0d-161">You can change the path of the executable (Setup.exe in the example) in the `Launch` method to point to its correct location, or customize the code to determine the location.</span></span> <span data-ttu-id="74c0d-162">A classe base `MmioChainer` fornece um método `Run()` de bloqueio que a classe derivada chama.</span><span class="sxs-lookup"><span data-stu-id="74c0d-162">The `MmioChainer` base class provides a blocking `Run()` method that the derived class calls.</span></span>  
  
    ```cpp  
    bool Launch(const CString& args)  
    {  
    CString cmdline = L"dotNetFx45_Full_x86_x64.exe -pipe TheSectionName " + args; // Customize with name and location of setup .exe that you want to run  
    STARTUPINFO si = {0};  
    si.cb = sizeof(si);  
    PROCESS_INFORMATION pi = {0};  
  
    // Launch the Setup.exe that installs the .NET Framework 4.5  
    BOOL bLaunchedSetup = ::CreateProcess(NULL,   
     cmdline.GetBuffer(),  
     NULL, NULL, FALSE, 0, NULL, NULL,   
     &si,  
     &pi);  
  
    // If successful   
    if (bLaunchedSetup != 0)  
    {  
    IProgressObserver& observer = dynamic_cast<IProgressObserver&>(*this);  
    Run(pi.hProcess, observer);  
  
    ……………………..   
    return (bLaunchedSetup != 0);  
    }  
    ```  
  
-   <span data-ttu-id="74c0d-163">O método `Send` intercepta e processa as mensagens.</span><span class="sxs-lookup"><span data-stu-id="74c0d-163">The `Send` method intercepts and processes the messages.</span></span>  <span data-ttu-id="74c0d-164">Nesta versão do .NET Framework, a única mensagem com suporte é a mensagem de fechar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74c0d-164">In this version of the .NET Framework, the only supported message is the close application message.</span></span>  
  
    ```cpp  
            // SendMessage  
            //  
            // Send a message and wait for the response.  
            // dwMessage: Message to send  
            // pData: The buffer to copy the data to  
            // dwDataLength: Initially a pointer to the size of pBuffer.  Upon successful call, the number of bytes copied to pBuffer.  
            //--------------------------------------------------------------  
        virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength)  
        {  
            DWORD dwResult = 0;  
            printf("recieved message: %d\n", dwMessage);  
            // Handle message  
            switch (dwMessage)  
            {  
            case MMIO_CLOSE_APPS:  
                {  
                    printf("    applications are holding files in use:\n");  
                    IronMan::MmioCloseApplications* applications = reinterpret_cast<IronMan::MmioCloseApplications*>(pData);  
                    for(DWORD i = 0; i < applications->m_dwApplicationsSize; i++)  
                    {  
                        printf("      %ls (%d)\n", applications->m_applications[i].m_szName, applications->m_applications[i].m_dwPid);  
                    }  
  
                    printf("    should appliations be closed? (Y)es, (N)o, (R)efresh : ");  
                    while (dwResult == 0)  
                    {  
                        switch (toupper(getwchar()))  
                        {  
                        case 'Y':  
                            dwResult = IDYES;  // Close apps  
                            break;  
                        case 'N':  
                            dwResult = IDNO;  
                            break;  
                        case 'R':  
                            dwResult = IDRETRY;  
                            break;  
                        }  
                    }  
                    printf("\n");  
                    break;  
                }  
            default:  
                break;  
            }  
            printf("  response: %d\n  ", dwResult);  
            return dwResult;  
        }  
    };  
    ```  
  
-   <span data-ttu-id="74c0d-165">Os dados de progresso são um `char` sem sinal entre 0 (0%) e 255 (100%).</span><span class="sxs-lookup"><span data-stu-id="74c0d-165">Progress data is an unsigned `char` between 0 (0%) and 255 (100%).</span></span>  
  
    ```cpp  
    private: // IProgressObserver  
        virtual void OnProgress(unsigned char ubProgressSoFar)  
        {…………  
       }  
    ```  
  
-   <span data-ttu-id="74c0d-166">O HRESULT é passado para o método `Finished`.</span><span class="sxs-lookup"><span data-stu-id="74c0d-166">The HRESULT is passed to the `Finished` method.</span></span>  
  
    ```cpp  
    virtual void Finished(HRESULT hr)  
    {  
    // This HRESULT is communicated over MMIO and may be different than process  
    // Exit code of the Chainee Setup.exe itself  
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);  
    }  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="74c0d-167">O [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistribuível normalmente grava muitas mensagens de progresso e uma única mensagem que indica a conclusão (no lado do encadeador).</span><span class="sxs-lookup"><span data-stu-id="74c0d-167">The [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable typically writes many progress messages and a single message that indicates completion (on the chainer side).</span></span> <span data-ttu-id="74c0d-168">Ele também lê assincronamente, procurando registros `Abort`.</span><span class="sxs-lookup"><span data-stu-id="74c0d-168">It also reads asynchronously, looking for `Abort` records.</span></span> <span data-ttu-id="74c0d-169">Se receber um registro `Abort`, ele cancelará a instalação e gravará um registro concluído com E_ABORT como seus dados depois que a instalação tiver sido cancelada e as operações de instalação tiverem sido revertidas.</span><span class="sxs-lookup"><span data-stu-id="74c0d-169">If it receives an `Abort` record, it cancels the installation, and writes a finished record with E_ABORT as its data after the installation has been aborted and setup operations have been rolled back.</span></span>  
  
 <span data-ttu-id="74c0d-170">Um servidor típico cria um nome de arquivo MMIO aleatório, cria o arquivo (conforme mostrado no exemplo de código anterior, na `Server::CreateSection`) e inicia o redistribuível usando o método `CreateProcess` e passando o nome do pipe com a opção `-pipe someFileSectionName`.</span><span class="sxs-lookup"><span data-stu-id="74c0d-170">A typical server creates a random MMIO file name, creates the file (as shown in the previous code example, in `Server::CreateSection`), and launches the redistributable by using the `CreateProcess` method and passing the pipe name with the `-pipe someFileSectionName` option.</span></span> <span data-ttu-id="74c0d-171">O servidor deve implementar os métodos `OnProgress`, `Send` e `Finished` com código específico da interface do usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="74c0d-171">The server should implement `OnProgress`, `Send`, and `Finished` methods with application UI-specific code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74c0d-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74c0d-172">See Also</span></span>  
 [<span data-ttu-id="74c0d-173">Guia de implantação para desenvolvedores</span><span class="sxs-lookup"><span data-stu-id="74c0d-173">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [<span data-ttu-id="74c0d-174">Implantação</span><span class="sxs-lookup"><span data-stu-id="74c0d-174">Deployment</span></span>](../../../docs/framework/deployment/index.md)
