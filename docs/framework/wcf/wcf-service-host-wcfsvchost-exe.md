---
title: "Host de serviço do WCF (WcfSvcHost.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
caps.latest.revision: "27"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 709e73b0fe665d836dfa50a630de35d955e110eb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-service-host-wcfsvchostexe"></a>Host de serviço do WCF (WcfSvcHost.exe)
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]Host de serviço (WcfSvcHost.exe) permite que você inicie a [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] depurador (F5) para hospedar e testar um serviço que você implementou automaticamente. Você pode testar, em seguida, o serviço usando [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] cliente de teste (WcfTestClient.exe) ou seu próprio cliente, para localizar e corrigir todos os possíveis erros.  
  
## <a name="wcf-service-host"></a>Host de serviço do WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Host de serviço enumera os serviços em um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projeto de serviço carrega a configuração do projeto e instancia um host para cada serviço que encontrar. A ferramenta é integrada ao [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] por meio de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] modelo de serviço e é invocado quando você inicia a depuração de seu projeto.  
  
 Usando [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host de serviço, você pode hospedar uma [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service (em um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projeto de biblioteca de serviço) sem escrever código extra ou confirmar a um host específico durante o desenvolvimento.  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Host de serviço não dá suporte a confiança parcial. Se você quiser usar um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço em confiança parcial, não use o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] modelo de projeto de biblioteca de serviço em [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] para criar o serviço. Em vez disso, crie um novo site no [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] escolhendo o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] modelo de site de serviço, que pode hospedar o serviço em um servidor Web no qual [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] há suporte para a relação de confiança parcial.  
  
## <a name="project-types-hosted-by-wcf-service-host"></a>Tipos de projeto hospedados pelo Host de serviço do WCF  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Host de serviço pode hospedar o seguinte [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] tipos de projeto de biblioteca de serviço: [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] biblioteca de serviço, biblioteca de serviço de fluxo de trabalho sequencial, biblioteca de serviço de fluxo de trabalho de máquina de estado e biblioteca de serviço de distribuição. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Host de serviço também pode hospedar os serviços que podem ser adicionados a um projeto de biblioteca de serviço usando o **Adicionar Item** funcionalidade. Isso inclui [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service, serviço de máquina de estado do WF, WF Sequential Service, serviço de máquina de estado do XAML WF e serviço sequencial do XAML WF.  
  
 No entanto, você deve observar que a ferramenta não irá ajudá-lo a configurar um host. Para esta tarefa, você deve editar manualmente o arquivo App. config. A ferramenta também não validar os arquivos de configuração definida pelo usuário.  
  
> [!CAUTION]
>  Você não deve usar [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host de serviço para serviços em um ambiente de produção, pois ele não foi projetado para essa finalidade.  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Host de serviço não dá suporte a confiabilidade, segurança e requisitos de capacidade de gerenciamento do ambiente. Em vez disso, use o IIS porque ele fornece recursos de monitoramento e maior confiabilidade e é a solução preferida para serviços de hospedagem. Após a conclusão do desenvolvimento de seus serviços, você deve migrar os serviços de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host de serviço do IIS.  
  
## <a name="scenarios-for-using-wcf-service-host-inside-visual-studio"></a>Cenários para usar o Host de serviço do WCF no Visual Studio  
 A tabela a seguir lista todos os parâmetros no **argumentos de linha de comando** caixa de diálogo que pode ser encontrada clicando com o seu projeto no **Gerenciador de soluções** em [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], selecionando  **Propriedades**, em seguida, selecionando o **depurar** guia e clicando em **Iniciar projeto**. Esses parâmetros são úteis na configuração [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host de serviço.  
  
|Parâmetro|Significado|  
|---------------|-------------|  
|`/client`|Um parâmetro opcional que especifica o caminho para um executável a ser executado depois que os serviços hospedados. Isso inicia [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] cliente de teste a seguir de hospedagem.|  
|`/clientArg`|Especifique uma cadeia de caracteres como um argumento que é passado para o aplicativo de cliente personalizadas.|  
|`/?`|Exibe o texto de Ajuda.|  
  
#### <a name="using-wcf-test-client"></a>Usando o cliente de teste do WCF  
 Depois de criar um novo [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projeto de serviço e pressione F5 para iniciar o depurador [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host de serviço inicia a hospedagem de todos os serviços encontrados em seu projeto. [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]Cliente de teste automaticamente abre e exibe uma lista de pontos de extremidade de serviço definidos no arquivo de configuração. Na janela principal, você pode testar os parâmetros e invocar o serviço.  
  
 Para certificar-se de que [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] cliente de teste é usado, clique no seu projeto no **Gerenciador de soluções** na [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], selecione **propriedades**, em seguida, selecione o **depurar**guia. Clique em **Iniciar projeto** e certifique-se de que o seguinte é exibido no **argumentos de linha de comando** caixa de diálogo.  
  
 `/client:WcfTestClient.exe`  
  
#### <a name="using-a-custom-client"></a>Usando um cliente personalizado  
 Para usar um cliente personalizado, clique com botão direito no projeto **Gerenciador de soluções** na [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], selecione **propriedades**, em seguida, selecione o **depurar** guia. Clique em **Iniciar projeto** e editar o `/client` parâmetro o **argumentos de linha de comando** caixa de diálogo para apontar para o cliente personalizado, conforme indicado no exemplo a seguir.  
  
 `/client:"path/CustomClient.exe"`  
  
 Quando você pressionar F5 para iniciar o serviço novamente, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host de serviço é iniciado automaticamente seu cliente personalizado quando você iniciar o depurador.  
  
 Você também pode usar o `/clientArg:` para especificar uma cadeia de caracteres como um argumento que é passado para o aplicativo cliente personalizado, conforme indicado no exemplo a seguir.  
  
 `/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`  
  
 Por exemplo, se você estiver usando o modelo de biblioteca de serviço de distribuição, você pode usar os seguintes argumentos de linha de comando,  
  
 `/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`  
  
#### <a name="specifying-no-client"></a>Não especificar nenhum cliente  
 Para especificar que nenhum cliente será usado depois [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço de hospedagem, clique no seu projeto no **Gerenciador de soluções** na [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], selecione **propriedades**, em seguida, selecione o **Depurar** guia. Clique em **Iniciar projeto** e deixar o **argumentos de linha de comando** caixa de diálogo em branco.  
  
#### <a name="using-a-custom-host"></a>Usando um Host personalizado  
 Para usar um host personalizado, clique com botão direito no projeto **Gerenciador de soluções** na [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], selecione **propriedades**, em seguida, selecione o **depurar** guia. Clique em **Iniciar programa externo** e insira o caminho completo para o host personalizado. Você também pode usar o **argumentos de linha de comando** caixa de diálogo para especificar os argumentos a serem passados para o host.  
  
## <a name="wcf-service-host-user-interface"></a>Interface de usuário de Host de serviço do WCF  
 Quando você invoca inicialmente [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host de serviço (pressionando F5 dentro [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]), o **Host de serviço WCF** janela será aberta automaticamente. Quando [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host de serviço está em execução, o ícone do programa é exibido na área de notificação. Clique duas vezes no ícone para abrir o **Host de serviço WCF** janela  
  
 Quando ocorrem erros durante a hospedagem de serviços, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] caixa de diálogo de Host de serviço será aberta para exibir informações relevantes.  
  
 O **Host de serviço WCF** janela principal contém dois menus:  
  
-   **Arquivo**: contém o **fechar** e **Exit** comandos. Quando você clica em **fechar**, o **Host de serviço WCF** caixa de diálogo é fechada, mas os serviços continuarão a ser hospedado. Quando você clica em **Exit**, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host de serviço também é desligado. Isso também interrompe todos os serviços hospedados.  
  
-   **Ajuda**: contém o **sobre** comando que contém informações de versão. Ele também contém o **ajuda** comando que pode abrir um arquivo de Ajuda.  
  
 O principal **Host de serviço WCF** janela contém duas áreas:  
  
-   A primeira área é **Service**. Ele contém uma lista que exibe informações básicas de todos os serviços. As informações incluem:  
  
    -   **Serviço**: lista todos os serviços.  
  
    -   **Status**: lista o status do serviço. Os valores válidos são "Iniciado", "Stopped" e "Error".  
  
    -   **Endereço de metadados**: exibe o endereço de metadados dos serviços.  
  
-   A segunda área é **informações adicionais**. Ele exibe uma explicação detalhada sobre o status do serviço quando a linha específica do serviço é selecionada no **Service** área. Se o status de erro, você pode exibir a mensagem de erro completa na tela.  
  
## <a name="stopping-wcf-service-host"></a>Parando o Host de serviço do WCF  
 Você pode desligar [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host de serviço de quatro maneiras a seguir:  
  
-   Parar a sessão de depuração em [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
-   Selecione **sair** do **arquivo** menu o **Host de serviço WCF** janela.  
  
-   Selecione **Exit** no menu de contexto de [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ícone de bandeja do Host de serviço na área de notificação do sistema.  
  
-   Saída [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] cliente de teste se ele está sendo usado.  
  
## <a name="using-service-host-without-administrator-privilege"></a>Usando o Host de serviço sem privilégios de administrador  
 Para permitir que usuários sem privilégios de administrador para desenvolver [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services, uma ACL (lista de controle de acesso) é criada para o namespace "http://+:8731/Design_Time_Addresses" durante a instalação do [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. A ACL é definida como (IU), que inclui todos os usuários interativos, conectados à máquina. Administradores podem adicionar ou remover usuários dessa ACL ou abrir portas adicionais. Essa ACL permite que os usuários usem o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Host automática de serviço (wcfSvcHost.exe) sem conceder privilégios de administrador.  
  
 Você pode modificar o acesso usando a ferramenta netsh.exe [!INCLUDE[wv](../../../includes/wv-md.md)] na conta de administrador com privilégios elevados. Este é um exemplo de uso netsh.exe.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Para obter mais informações sobre netsh.exe, consulte "[como usar a ferramenta Netsh.exe e as opções de linha de comando](http://go.microsoft.com/fwlink/?LinkId=97877)".  
  
## <a name="see-also"></a>Consulte também  
 [WCF Test Client (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md) [Cliente de teste do WCF (WcfTestClient.exe)]
