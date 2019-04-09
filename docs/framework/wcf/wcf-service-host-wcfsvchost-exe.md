---
title: Host de serviço do WCF (WcfSvcHost.exe)
ms.date: 03/30/2017
ms.assetid: 8643a63d-a357-4c39-bd6c-cdfdf71e370e
ms.openlocfilehash: d9a086b3a6ae0ece3b1b45161402ce058e1fb447
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193012"
---
# <a name="wcf-service-host-wcfsvchostexe"></a>Host de serviço do WCF (WcfSvcHost.exe)
Host de serviço do Windows Communication Foundation (WCF) (WcfSvcHost.exe) permite que você iniciar o depurador do Visual Studio (F5) para hospedar automaticamente e testar um serviço que você implementou. Em seguida, você pode testar o serviço usando o cliente de teste do WCF (WcfTestClient.exe) ou seu próprio cliente, para encontrar e corrigir os erros em potencial.  
  
## <a name="wcf-service-host"></a>Host de serviço WCF  
 Host de serviço WCF enumera os serviços em um projeto de serviço do WCF, carrega a configuração do projeto e cria uma instância de um host para cada serviço que encontrar. A ferramenta é integrada ao Visual Studio por meio do modelo de serviço do WCF e é invocada quando você inicia a depuração de seu projeto.  
  
 Usando o Host de serviço WCF, você pode hospedar um serviço WCF (em um projeto de biblioteca de serviço do WCF) sem gravar código extra ou confirmar a um host específico durante o desenvolvimento.  
  
> [!NOTE]
>  Host de serviço do WCF não oferece suporte a confiança parcial. Se você quiser usar um serviço WCF em confiança parcial, não use o modelo de projeto de biblioteca de serviço do WCF no Visual Studio para criar seu serviço. Em vez disso, crie um novo site no Visual Studio escolhendo o modelo de site do serviço WCF, que pode hospedar o serviço em um servidor Web no qual a confiança parcial do WCF é suportado.  
  
## <a name="project-types-hosted-by-wcf-service-host"></a>Tipos de projeto hospedados pelo Host de serviço do WCF  
 Host de serviço WCF pode hospedar os seguintes tipos de projeto de biblioteca de serviço WCF: WCF Service Library, biblioteca de serviço de fluxo de trabalho sequencial, State Machine Workflow Service Library e Syndication Service Library. Host de serviço WCF também pode hospedar os serviços que podem ser adicionados a um projeto de biblioteca de serviço usando o **Adicionar Item** funcionalidade. Isso inclui o serviço WCF, o serviço de máquina de estado do WF, WF Sequential Service, serviço de máquina de estado do XAML WF e XAML WF Sequential Service.  
  
 No entanto, você deve observar que a ferramenta não ajudará a configurar um host. Para essa tarefa, você deve editar manualmente o arquivo App. config. A ferramenta também não valida arquivos de configuração definido pelo usuário.  
  
> [!CAUTION]
>  Você não deve usar o Host de serviço do WCF para hospedar os serviços em um ambiente de produção, pois ele não foi desenvolvido para essa finalidade.  Host de serviço do WCF não oferece suporte a confiabilidade, segurança e requisitos de capacidade de gerenciamento desse ambiente. Em vez disso, use o IIS, pois ele fornece recursos de monitoramento e confiabilidade superior e é a melhor solução para hospedar os serviços. Após a conclusão do desenvolvimento de seus serviços, você deve migrar os serviços do Host de serviço do WCF no IIS.  
  
## <a name="scenarios-for-using-wcf-service-host-inside-visual-studio"></a>Cenários para usar o Host de serviço do WCF dentro do Visual Studio  
 A tabela a seguir lista todos os parâmetros na **argumentos de linha de comando** caixa de diálogo que pode ser encontrada clicando com o seu projeto no **Solutions Explorer** no Visual Studio, selecionando **As propriedades**, em seguida, selecionando o **depurar** guia e clicando em **Iniciar projeto**. Esses parâmetros são úteis na configuração do Host de serviço WCF.  
  
|Parâmetro|Significado|  
|---------------|-------------|  
|`/client`|Um parâmetro opcional que especifica o caminho para um executável para ser executado depois que os serviços são hospedados. Isso inicia o cliente de teste do WCF hospeda a seguir.|  
|`/clientArg`|Especifique uma cadeia de caracteres como um argumento que é passado para o aplicativo de cliente personalizadas.|  
|`/?`|Exibe o texto de Ajuda.|  
  
#### <a name="using-wcf-test-client"></a>Usando o cliente de teste do WCF  
 Depois de criar um novo projeto de serviço do WCF e pressione F5 para iniciar o depurador, o Host de serviço WCF inicia a hospedagem de todos os serviços que ele se encontra em seu projeto. Cliente de teste do WCF automaticamente abre e exibe uma lista de pontos de extremidade de serviço definidos no arquivo de configuração. Na janela principal, você pode testar os parâmetros e invocar o serviço.  
  
 Para certificar-se de que o cliente de teste do WCF é usado, com o botão direito no projeto **Gerenciador de soluções** no Visual Studio, selecione **Properties**, em seguida, selecione o **depurar** guia. Clique em **Iniciar projeto** e certifique-se de que o seguinte será exibido na **argumentos de linha de comando** caixa de diálogo.  
  
 `/client:WcfTestClient.exe`  
  
#### <a name="using-a-custom-client"></a>Usando um cliente personalizado  
 Para usar um cliente personalizado, clique com botão direito no projeto **Gerenciador de soluções** no Visual Studio, selecione **Properties**, em seguida, selecione o **depurar** guia. Clique em **Iniciar projeto** e edite o `/client` parâmetro no **argumentos de linha de comando** caixa de diálogo para apontar para seu cliente personalizado, conforme indicado no exemplo a seguir.  
  
 `/client:"path/CustomClient.exe"`  
  
 Quando você pressiona F5 para iniciar o serviço novamente, o Host de serviço WCF inicia automaticamente personalizadas do cliente quando você iniciar o depurador.  
  
 Você também pode usar o `/clientArg:` parâmetro para especificar uma cadeia de caracteres como um argumento que é passado para o aplicativo cliente personalizado, conforme indicado no exemplo a seguir.  
  
 `/client:"path/CustomClient.exe" /clientArg:"arguments that are passed to Client"`  
  
 Por exemplo, se você estiver usando o modelo Syndication Service Library, você pode usar os seguintes argumentos de linha de comando,  
  
 `/client:iexplore.exe /clientArgs:http://localhost:8731/Design_Time_Addresses/Feed1/`  
  
#### <a name="specifying-no-client"></a>Não especificar nenhum cliente  
 Para especificar que nenhum cliente será usado após a hospedagem de serviço do WCF, clique com botão direito no projeto **Gerenciador de soluções** no Visual Studio, selecione **Properties**, em seguida, selecione o **depurar** guia. Clique em **Iniciar projeto** e deixe o **argumentos de linha de comando** caixa de diálogo em branco.  
  
#### <a name="using-a-custom-host"></a>Usando um Host personalizado  
 Para usar um host personalizado, clique com botão direito no projeto **Gerenciador de soluções** no Visual Studio, selecione **Properties**, em seguida, selecione o **depurar** guia. Clique em **Iniciar programa externo** e digite o caminho completo para o host personalizado. Você também pode usar o **argumentos de linha de comando** caixa de diálogo para especificar os argumentos a serem passados para o host.  
  
## <a name="wcf-service-host-user-interface"></a>Interface de usuário do Host de serviço do WCF  
 Quando você invoca inicialmente Host de serviço WCF (pressionando F5 no Visual Studio), o **Host de serviço WCF** janela é aberta automaticamente. Quando o Host de serviço WCF estiver em execução, o ícone do programa aparece na área de notificação. Clique duas vezes no ícone para abrir o **Host de serviço WCF** janela  
  
 Quando ocorrem erros durante a hospedagem de serviços, a caixa de diálogo de Host de serviço WCF será aberto para exibir as informações relevantes.  
  
 O **Host de serviço WCF** janela principal contém dois menus:  
  
-   **Arquivo**: Contém o **feche** e **sair** comandos. Quando você clica em **feche**, o **Host de serviço WCF** caixa de diálogo é fechada, mas os serviços continuarão a ser hospedado. Quando você clica em **Exit**, Host de serviço WCF também é desligado. Isso também interrompe todos os serviços hospedados.  
  
-   **Ajudar a**: Contém o **sobre** comando que contém informações de versão. Ele também contém o **ajudar** comando que pode abrir um arquivo de Ajuda.  
  
 A principal **Host de serviço WCF** janela contém duas áreas:  
  
-   É a primeira área **serviço**. Ele contém uma lista que exibe informações básicas de todos os serviços. As informações incluem:  
  
    -   **Serviço**: Lista todos os serviços.  
  
    -   **status**: Lista o status do serviço. Valores válidos são "Iniciado", "Stopped" e "Error".  
  
    -   **Endereço de metadados**: Exibe o endereço de metadados dos serviços.  
  
-   A segunda área é **informações adicionais**. Ele exibe uma explicação detalhada sobre o status do serviço quando a linha de serviço específica for selecionada na **serviço** área. Se o status de erro, você pode exibir a mensagem de erro completa na tela.  
  
## <a name="stopping-wcf-service-host"></a>Parando o Host de serviço do WCF  
 Você pode desligar o Host de serviço WCF das quatro seguintes maneiras:  
  
-   Pare a sessão de depuração no Visual Studio.  
  
-   Selecione **Exit** da **arquivo** menu no **Host de serviço WCF** janela.  
  
-   Selecione **Exit** no menu de contexto do ícone de bandeja do Host de serviço WCF na área de notificação do sistema.  
  
-   Saia do cliente de teste do WCF se ele está sendo usado.  
  
## <a name="using-service-host-without-administrator-privilege"></a>Usando o Host de serviço sem privilégio de administrador  
 Para permitir que usuários sem privilégios de administrador desenvolver serviços WCF, uma ACL (lista de controle de acesso) é criada para o namespace "http://+:8731/Design_Time_Addresses" durante a instalação do Visual Studio. A ACL é definida como (UI), que inclui todos os usuários interativos, conectados à máquina. Os administradores podem adicionar ou remover usuários dessa ACL ou abrir portas adicionais. Essa ACL permite que os usuários usem o Host de automático de serviço do WCF (wcfSvcHost.exe) sem conceder privilégios de administrador.  
  
 Você pode modificar o acesso usando a ferramenta netsh.exe no [!INCLUDE[wv](../../../includes/wv-md.md)] sob a conta de administrador com privilégios elevados. O exemplo a seguir é um exemplo de uso netsh.exe.  
  
```  
netsh http add urlacl url=http://+:8001/MyService user=<domain>\<user>  
```  
  
 Para obter mais informações sobre netsh.exe, consulte "[como usar a ferramenta de Netsh.exe e as opções de linha de comando](https://go.microsoft.com/fwlink/?LinkId=97877)".  
  
## <a name="see-also"></a>Consulte também

- [Cliente de Teste do WCF (WcfTestClient.exe)](../../../docs/framework/wcf/wcf-test-client-wcftestclient-exe.md)
