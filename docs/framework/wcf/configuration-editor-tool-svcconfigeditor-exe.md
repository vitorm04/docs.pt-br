---
title: Ferramenta Configuration Editor (SvcConfigEditor.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
ms.openlocfilehash: e4b54026c71e18e4011661c5cad2ca95dfcb733e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979934"
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a>Ferramenta Configuration Editor (SvcConfigEditor.exe)
O Editor de configuração de serviço do Windows Communication Foundation (WCF) (SvcConfigEditor.exe) permite que os administradores e desenvolvedores criar e modificar definições de configuração para serviços WCF usando uma interface gráfica do usuário. Com essa ferramenta, você pode gerenciar as configurações para associações, comportamentos, serviços e diagnóstico do WCF sem a necessidade de editar diretamente os arquivos de configuração XML.  
  
 Editor de configuração de serviço pode ser encontrado na pasta C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.  
  
## <a name="the-wcf-configuration-editor"></a>O Editor de configuração do WCF  
 Editor de configuração de serviço é fornecido com um assistente que orienta você pelas etapas na configuração de um cliente ou um serviço WCF. É altamente recomendável usar o assistente em vez de editor diretamente.  
  
 Se você já tiver alguns arquivos de configuração que estão em conformidade com o esquema padrão do System. Configuration, você pode gerenciar configurações específicas para associações, o comportamento, serviços e diagnóstico com a interface do usuário. O Service Configuration Editor permite que você gerencie as configurações para arquivos de configuração do WCF existentes, bem como arquivos executáveis, serviços COM+ e serviços hospedados na Web. Ao abrir um serviço Web hospedado com o Service Configuration Editor, o serviço do próprio configuração e seções de configurações herdadas de nós de nível superiores são mostradas.  
  
 Porque as definições de configuração do WCF estão localizadas no `<system.serviceModel>` seção do arquivo de configuração, o editor funciona exclusivamente com o conteúdo desse elemento e não acessa outros elementos no mesmo arquivo. Você pode navegar diretamente até os arquivos de configuração existente ou você pode selecionar um assembly que contém um serviço, um diretório virtual ou um serviço COM+. O editor carrega o arquivo de configuração para o serviço específico e permite que o usuário adicionar novos elementos ou editar existentes elementos aninhados no `<system.serviceModel>` seção do arquivo de configuração.  
  
 O editor dá suporte ao IntelliSense e impõe a conformidade de esquema. A saída resultante é garantida para estar em conformidade com o esquema do arquivo de configuração e para ter valores de dados sintaticamente correto. No entanto, o editor não garante que o arquivo de configuração é semanticamente válido. Em outras palavras, o editor não garante que o arquivo de configuração pode trabalhar com o serviço, que ele configura.  
  
> [!CAUTION]
>  O editor não é possível limpar um elemento de configuração do arquivo de configuração depois de modificar o elemento. Por exemplo, se você usar o editor para definir o nome do ponto de extremidade para uma cadeia de caracteres não vazia e salvá-lo, o arquivo de configuração tem o conteúdo a seguir, conforme mostrado no exemplo a seguir.  
>   
>  `<endpoint binding="basicHttpBinding" name="somename" />`  
>   
>  Se você tentar remover o nome, defini-la para uma cadeia de caracteres vazia e salvar o arquivo, o arquivo de configuração ainda contém o `name` de atributo, conforme mostrado no exemplo a seguir.  
>   
>  `<endpoint binding="basicHttpBinding" name="" />`  
>   
>  Para limpar o atributo, você deve editar manualmente o elemento usando outro editor de texto.  
>   
>  Seja especialmente cauteloso com esse problema quando você usa o `issueToken` elemento o `clientCredential` comportamento de ponto de extremidade. Especificamente, o `address` atributo do seu `localIssuer` subelemento não deve ser uma cadeia de caracteres vazia. Se você tiver modificado o `address` usando o Editor de configuração de atributo e removê-la completamente, você deve fazer isso usando uma ferramenta que não seja o Editor. Caso contrário, o atributo contém uma cadeia de caracteres vazia e seu aplicativo gera uma exceção.  
  
## <a name="using-the-configuration-editor"></a>Usando o Editor de configuração  
 O Editor de configuração de serviço podem ser encontrado no seguinte local de instalação do SDK do Windows:  
  
 C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe  
  
 Depois de iniciar o Editor de configuração de serviço, você pode usar o **arquivo/abrir** menu para navegar para o serviço ou o assembly que você deseja gerenciar. Você pode abrir arquivos diretamente, navegue para os serviços WCF /COM+ e abrem arquivos de configuração para serviços hospedados na Web de configuração.  
  
 Interface do usuário do Service Configuration Editor é dividido nas seguintes áreas:  
  
-   Painel de exibição de árvore, que exibe os elementos de configuração em uma estrutura de árvore à esquerda. Você pode executar operações na árvore clicando-se a nós.  
  
-   Painel de tarefas, que exibe tarefas comuns para elementos atuais no canto inferior esquerdo da janela  
  
-   Painel de detalhes, que exibe as configurações detalhadas do nó da configuração selecionada na exibição de árvore à direita.  
  
### <a name="opening-a-configuration-file"></a>Abrir um arquivo de configuração  
  
1. Iniciar o Editor de configuração de serviço por meio de uma janela de comando para navegar até o local de instalação do WCF e, em seguida, digite `SvcConfigEditor.exe`.  
  
2. Dos **arquivo** menu, selecione **abrir** e clique no tipo de arquivo que você deseja gerenciar.  
  
3. No **abrir** caixa de diálogo, navegue até o arquivo específico que você deseja gerenciar e clique duas vezes nele.  
  
 O visualizador segue o caminho de configuração direta e cria uma exibição da configuração mesclada automaticamente. Por exemplo, a configuração real de um serviço hospedado não é uma combinação de Machine. config e App. config. Todas as alterações são aplicadas para o arquivo ativo no SvcConfigEditor. Se você quiser editar um arquivo específico no caminho de configuração de mesclagem, você deve abri-lo diretamente.  
  
> [!NOTE]
>  Editor de configuração recarrega o arquivo de configuração atualmente aberto quando o último foi modificado fora do Editor. Quando isso acontece, todas as alterações que não são salvos permanentemente dentro do Editor são perdidas. Se o recarregamento acontece consistentemente, a causa mais provável é um serviço que acessa constantemente o arquivo de configuração, um software antivírus em execução em segundo plano, por exemplo. Para resolver esse problema, certifique-se de que o Editor de configuração é o único processo que pode acessar o arquivo quando ele é aberto.  
  
### <a name="services"></a>Serviços  
 O **Services** nó exibe todos os serviços atualmente atribuídos no arquivo de configuração. Cada subseção nó na árvore de corresponde a um subelemento da <`services`> elemento no arquivo de configuração.  
  
 Quando você clica no **Services** nó, você pode exibir ou executar tarefas no serviço de página de resumo no **detalhes** painel.  
  
#### <a name="creating-a-new-service-configuration"></a>Criando uma nova configuração de serviço  
 Você pode criar uma nova configuração de serviço das seguintes maneiras:  
  
-   Usando um assistente: Clique no link **criar um novo serviço...** no painel de tarefas ou página de resumo para iniciar o assistente. Você também pode fazer isso na **arquivo** -> menu **Adicionar Novo Item**.  
  
-   Crie manualmente: Você pode com o botão direito do **serviços** nó e escolha **novo serviço**.  
  
#### <a name="creating-a-new-service-endpoint-configuration"></a>Criando uma nova configuração de ponto de extremidade de serviço  
 Você pode criar uma nova configuração de ponto de extremidade de serviço das seguintes maneiras:  
  
-   Criar usando um assistente: clique no link **criar um novo ponto de extremidade de serviço...** no painel de tarefas ou página de resumo para iniciar o assistente. Você também pode fazer isso na **arquivo** -> menu **Adicionar Novo Item**.  
  
-   Crie manualmente: Depois que você criou um serviço, você pode clique com botão direito do **pontos de extremidade** nó e escolha "**novo ponto de extremidade de serviço**".  
  
#### <a name="editing-a-service-configuration"></a>Editando uma configuração de serviço  
  
1. Clique em uma **serviço** nó.  
  
2. Edite as configurações em grades de propriedades.  
  
#### <a name="editing-a-service-endpoint-configuration"></a>Editando uma configuração de ponto de extremidade de serviço  
  
1. Clique em uma **ponto de extremidade de serviço** nó.  
  
2. Edite as configurações em grades de propriedades.  
  
#### <a name="adding-a-base-address"></a>Adicionar um endereço de Base  
  
1. Clique o **Host** nó.  
  
2. Clique o **novo...** botão de **endereços de Base** seção.  
  
3. Digite o endereço básico URI na caixa de diálogo.  
  
4. Clique em **OK**.  
  
> [!NOTE]
>  Você não pode editar o valor de [ \<baseAddressPrefixFilters >](../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) dentro dessa ferramenta. Para adicionar ou modificar esse elemento, você deve usar um editor de texto ou o Visual Studio.  
  
### <a name="client"></a>Cliente  
 O **cliente** nó exibe todos os pontos de extremidade do cliente no arquivo de configuração. Todos os nós na árvore de subpropriedades corresponde a um subelemento da <`client`> elemento no arquivo de configuração.  
  
 Quando você clica na **Client** nó, você pode exibir ou executar tarefas no cliente **página de resumo** no **painel de detalhes**.  
  
#### <a name="creating-a-new-client-endpoint-configuration"></a>Criando uma nova configuração de ponto de extremidade do cliente  
 Você pode criar uma nova configuração de ponto de extremidade do cliente das seguintes maneiras:  
  
-   Crie pelo Assistente: Clique no link **criar um novo cliente...** sobre o **painel de tarefas** no canto inferior esquerdo da janela, ou **página de resumo** para iniciar o assistente. Você também pode fazer isso na **arquivo** -> menu **Adicionar Novo Item**. O assistente solicita que você apontar para o local da configuração do serviço, do qual a configuração do cliente é gerada. Em seguida, você pode escolher o ponto de extremidade de serviço para se conectar ao.  
  
-   Crie manualmente: Clique com botão direito do **pontos de extremidade** nó sob **cliente**e escolha **novo ponto de extremidade do cliente**.  
  
#### <a name="editing-a-client-endpoint-configuration"></a>Editando uma configuração de ponto de extremidade do cliente  
  
1. Clique em uma **ponto de extremidade cliente** nó.  
  
2. Edite as configurações em grades de propriedades.  
  
### <a name="standard-endpoint"></a>Ponto de extremidade padrão  
 Pontos de extremidade padrão são pontos de extremidade especializados que tem um ou mais os aspectos do endereço, contrato e associação são definidas com valores padrão.  
  
 Essas configurações são armazenadas em do **ponto de extremidade padrão** nó. O **ponto de extremidade padrão** nó exibe todas as configurações de ponto de extremidade padrão no arquivo de configuração. Todos os nós na árvore de subpropriedades corresponde a um subelemento no `<standardEndpoints>` elemento no arquivo de configuração.  
  
 Quando você clica o **ponto de extremidade padrão** nó, você pode exibir ou executar tarefas no ponto de extremidade padrão **página de resumo** no **painel de detalhes**.  
  
#### <a name="creating-a-new-standard-endpoint-configuration"></a>Criando uma nova configuração de ponto de extremidade padrão  
 Você pode criar uma nova configuração de ponto de extremidade padrão das seguintes maneiras:  
  
-   Clique com botão direito do **ponto de extremidade padrão** nó e selecione **nova configuração de ponto de extremidade padrão...** Selecione o tipo de associação, na caixa de diálogo e clique em **Okey**.  
  
-   Selecione o **ponto de extremidade padrão** nó e clique em **nova configuração de ponto de extremidade padrão...** no **painel de tarefas** no canto inferior esquerdo da janela.  
  
 O **criando um novo ponto de extremidade padrão** caixa de diálogo exibe e lista todos os tipos de ponto de extremidade padrão.  
  
#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a>Exibir e editar uma configuração de ponto de extremidade padrão  
 Você pode abrir uma configuração de ponto de extremidade padrão para exibição e edição das seguintes maneiras:  
  
-   Clique para expandir a **ponto de extremidade padrão** nó e clique no nó de subpropriedades do respectivo ponto de extremidade.  
  
-   Clique o **ponto de extremidade padrão** nó e clique no respectivo ponto de extremidade no painel de detalhes.  
  
 Atributos para o ponto de extremidade são mostrados no painel direito para edição.  
  
#### <a name="deleting-a-standard-endpoint-configuration"></a>Excluindo uma configuração de ponto de extremidade padrão  
 Você pode excluir uma configuração de ponto de extremidade padrão das seguintes maneiras:  
  
-   Clique para expandir a **ponto de extremidade padrão** nó e o botão direito do mouse subnó o respectivo ponto de extremidade. Use o comando de contexto **Excluir configuração de ponto de extremidade padrão** para excluir o ponto de extremidade.  
  
-   Clique o **ponto de extremidade padrão** nó. No **tarefa** painel, clique em **Excluir configuração de ponto de extremidade padrão**.  
  
 Se o ponto de extremidade padrão é em usado, uma mensagem de aviso é exibida quando você tentar excluí-lo: **O ponto de extremidade padrão está em uso. Se você excluí-lo agora, certifique-se de excluir todas as suas referências em outras partes da configuração (por exemplo, no ponto de extremidade de serviço ou cliente). Caso contrário, a configuração será inválida e não pode ser aberta da próxima vez. Tem certeza de que deseja excluir o ponto de extremidade standard?"**  
  
### <a name="binding"></a>Associação  
 Configurações de associação são usadas para configurar as ligações nos pontos de extremidade. Essas configurações são armazenadas em do **associação** nó. Pontos de extremidade de fazer referência a configurações de associação por nome e vários pontos de extremidade podem fazer referência a uma configuração de associação única.  
  
 O **associações** nó exibe todas as configurações de associação no arquivo de configuração. Todos os nós na árvore de subpropriedades corresponde a um subelemento no <`bindings`> elemento no arquivo de configuração.  
  
 Quando você clica na **ligações** nó, você pode exibir ou executar tarefas na associação **página de resumo** no **painel de detalhes**.  
  
#### <a name="creating-a-new-binding-configuration"></a>Criando uma nova configuração de associação  
 Você pode criar uma nova configuração de associação das seguintes maneiras.  
  
-   Clique com botão direito do **ligações** nó e selecione **nova configuração de associação**... Selecione o tipo de associação, na caixa de diálogo e clique em **Okey**.  
  
-   Selecione o **ligações** nó e clique em **nova configuração de associação**... no **painel de tarefas** no canto inferior esquerdo da janela.  
  
-   No serviço ou cliente página Resumo, clique em **clique para criar** na **configuração de associação** campo para criar uma configuração de associação para o ponto de extremidade correspondente.  
  
#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a>Adicionando extensões de elemento de associação para uma associação personalizada  
  
1. Selecione a associação que você deseja adicionar um elemento de extensão para.  
  
2. Clique em **Adicionar**.  
  
3. Na lista de extensões disponíveis, selecione a extensão de elemento de associação que você deseja adicionar. Para selecionar vários itens, pressione a tecla CTRL ao mesmo tempo.  
  
4. Clique em **Adicionar**.  
  
#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a>Ajustar a posição de extensão em uma associação personalizada  
 Uma associação personalizada é uma coleção de elementos que formam uma pilha de associação. Cada elemento na pilha de associação tem seus próprios parâmetros de configuração. A ordem das extensões do elemento de associação em uma associação personalizada indica suas posições na pilha. Elementos na parte superior da pilha são aplicados primeiro. Para alterar a ordem:  
  
1. Selecione o nó de associação personalizada.  
  
2. Selecionar um elemento de extensão de associação na **posição de extensão de elemento de associação** seção.  
  
3. Use o **para cima** ou **para baixo** botão no lado esquerdo da lista para alterar a posição do elemento selecionado.  
  
#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a>Edição da configuração de extensões de elemento de associação em uma associação personalizada  
  
1. Selecione o nó de associação na árvore.  
  
2. Selecione a associação personalizada que contém o elemento que você deseja editar.  
  
3. Selecione a extensão de elemento de associação que você deseja editar. As configurações do elemento aparecem no painel direito, em que eles podem ser editados.  
  
### <a name="diagnostics"></a>Diagnóstico  
 O **diagnóstico** nó exibe todas as configurações de diagnóstico no arquivo de configuração. Ele permite ativar ou desativar a contadores de desempenho, habilitar ou desabilitar o Windows Management Instrumentation (WMI), configurar o rastreamento do WCF e configurar o log de mensagem do WCF. As configurações na **diagnósticos** nó correspondem ao <`system.diagnostics`> seção, e `<diagnostics>` seção `<system.serviceModel>` no arquivo de configuração.  
  
 Quando você clica na **diagnósticos** nó, você pode exibir ou executar tarefas nos diagnósticos **página de resumo** no **painel de detalhes**.  
  
#### <a name="configuring-performance-counters-and-wmi"></a>Configurar contadores de desempenho e o WMI  
  
1. Clique o **diagnóstico** nó.  
  
2. Clique em **ativar/desativar os contadores de desempenho**. O contador de desempenho tem três estados: Off (padrão), ServiceOnly e tudo. Ao clicar no link alterna a configuração entre esses três estados.  
  
#### <a name="configuring-wmi-provider"></a>Configurar o provedor WMI  
  
1. Clique o **diagnóstico** nó.  
  
2. Para habilitar o provedor WMI, clique o **habilitar o provedor de WMI** link.  
  
#### <a name="enabling-wcf-tracing"></a>Habilitar o rastreamento do WCF  
 Você pode criar um arquivo de rastreamento do WCF com propriedades padrão ou configurar um arquivo de rastreamento personalizado.  
  
1. Clique o **diagnóstico** nó.  
  
2. Clique em **habilitar o rastreamento**.  
  
3. Clique o **nível de rastreamento** link para ajustar o nível de rastreamento. Há seis níveis de rastreamento: Desativado, crítico, erro, aviso, informações e detalhado. O **rastreamento de atividades** e **atividade propagar** opção permitem que você use o recurso de rastreamento de atividades do WCF.  
  
4. Clique no nome do ouvinte de rastreamento para especificar as opções e o arquivo de rastreamento.  
  
#### <a name="enabling-wcf-logging"></a>Habilitando o log do WCF  
 Você pode criar um arquivo de rastreamento do WCF com propriedades padrão ou configurar um arquivo de rastreamento personalizado.  
  
1. Clique o **diagnóstico** nó.  
  
2. Clique em **habilitar o log de mensagem**.  
  
3. Clique o **nível de Log** link para ajustar o nível de log. Há três níveis de log: Malformado, serviço e transporte.  
  
4. Clique no nome do ouvinte para especificar o arquivo de log e opções.  
  
> [!NOTE]
>  Se você quiser que os logs de rastreamento e a mensagem a ser liberado automaticamente quando seu aplicativo é fechado, habilite a **liberação automática** opção.  
  
 O **diagnósticos** **página de resumo** permite realizar as tarefas mais comuns na configuração de diagnóstico. No entanto, se você quiser editar manualmente as configurações de fontes e ouvintes, você deve expandir o **diagnósticos** configurações de nó e edit no **Message Logging**, **ouvintes** e **Fontes** nó.  
  
#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a>Habilitar o rastreamento do WCF personalizado ou registro em log de mensagem  
  
1. Clique o **diagnóstico** nó e expandi-lo.  
  
2. Clique com botão direito do **ouvintes** nó e selecione **novo ouvinte**.  
  
3. Digite o nome de arquivo rastreamento na **InitData** campo. Você pode clicar na..." botão para procurar um caminho.  
  
4. Clicar a **TypeName** linha exibe um "..." botão. Clique neste botão para abrir o **navegador de tipo de ouvinte de rastreamento**, que pode ser usado para localizar os ouvintes de rastreamento pré-configurados que já estão instalados.  
  
5. Observe a **origem** seção. Clique em **adicionar** nesta seção para abrir uma caixa de diálogo com um menu suspenso, que lista as fontes de rastreamento disponíveis. Selecione uma fonte de rastreamento e clique em **Okey**.  
  
6. Para editar as configurações do log de mensagem, clique o **Message Logging** nó. Você pode editar as configurações na grade de propriedade.  
  
### <a name="advanced"></a>Avançado  
  
#### <a name="behaviors"></a>Comportamentos  
 O **comportamentos** nó exibe os comportamentos que são atualmente definidos no arquivo de configuração.  
  
 Configurações de comportamento são usadas para configurar comportamentos de pontos de extremidade e serviços. Essas configurações são armazenadas na **Advanced** nó sob **comportamentos de serviço** e **comportamentos de ponto de extremidade**. Comportamentos de serviço são usados por serviços; enquanto os comportamentos de ponto de extremidade por pontos de extremidade.  
  
 Os comportamentos são uma coleção de elementos de extensão que uma pilha. O elemento na parte superior da pilha é aplicado primeiro. Cada elemento de extensão pode ter sua própria configuração.  
  
##### <a name="creating-a-new-behavior-configuration"></a>Criando uma nova configuração de comportamento  
 Você pode criar uma nova configuração de comportamento de duas maneiras.  
  
-   Clique em um de nós do comportamento e selecione "**nova configuração de comportamento...**  
  
-   Selecione um de nós do comportamento e clique no **nova configuração de comportamento**... no **painel de tarefas** no canto inferior esquerdo da janela.  
  
##### <a name="adding-behavior-element-extensions-to-a-behavior"></a>Adicionando extensões de elemento de comportamento a um comportamento  
  
1. Selecione um de nós do comportamento.  
  
2. Selecione o comportamento que você deseja editar.  
  
3. Clique em **Adicionar**.  
  
4. Na lista de extensões disponíveis, selecione a extensão de elemento de comportamento que você deseja adicionar.  
  
5. Clique em **Adicionar**.  
  
##### <a name="adjusting-the-extension-position-in-a-behavior"></a>Ajustar a posição de extensão em um comportamento  
 Os comportamentos são coleções de elementos que formam uma pilha. Cada elemento na pilha tem sua própria configuração. A ordem das extensões de elemento do comportamento em um comportamento indica suas posições na pilha. Elementos na parte superior da pilha são aplicados primeiro. Para alterar a ordem:  
  
1. Selecione um de nós do comportamento.  
  
2. Selecione o comportamento que você deseja editar.  
  
3. Selecione um elemento de extensão de comportamento na **posição de extensão de elemento de comportamento** seção.  
  
4. Use o **para cima** ou **para baixo** botão no lado esquerdo da lista para alterar a posição do elemento selecionado.  
  
##### <a name="editing-the-configuration-of-behavior-element-extensions"></a>Editando a configuração das extensões de elemento de comportamento  
  
1. Selecione um de nós de comportamento na árvore.  
  
2. Selecione o comportamento que contém o elemento que você deseja editar.  
  
3. Selecione a extensão de elemento de comportamento que você deseja editar. As configurações do elemento aparecem no painel direito, em que eles podem ser editados.  
  
#### <a name="protocolmapping"></a>protocolMapping  
 Esta seção permite que você defina tipos de associação para diferentes protocolos como http, tcp, MSMQ ou NET. pipe, por meio do mapeamento definido entre esquemas de endereço de protocolo e as possíveis associações de padrão. Você também pode adicionar novos mapeamentos para outros protocolos.  
  
#### <a name="extensions"></a>Extensões  
 Novas extensões de associação, as extensões de elemento de associação, extensões de ponto de extremidade padrão e extensões de comportamento podem ser registradas para uso na configuração do WCF. As extensões são pares de nome/tipo. O nome define o nome da extensão de configuração, enquanto o tipo implementa a extensão. Há quatro tipos de extensões:  
  
-   As extensões de associação definem um tipo de associação inteira. Exemplo: `basicHttpBinding`.  
  
-   Extensões de elemento de associação definem um elemento de uma associação. Exemplo: `textMessageEncoding`.  
  
-   Extensões de ponto de extremidade padrão definem um ponto de extremidade padrão inteiro. Exemplo: `discoveryEndpoint`.  
  
-   Extensões de elemento de comportamento definem um elemento de um comportamento. Exemplo: `clientVia`.  
  
 Extensões que foram registradas na configuração podem ser usadas como qualquer outro componente do WCF do mesmo tipo.  
  
##### <a name="adding-a-new-extension"></a>Adicionando uma nova extensão  
 Selecione um de nós de extensão em nós Avançado:  
  
1. Clique em **Novo**.  
  
2. Insira um nome e tipo.  
  
3. Clique em **OK**.  
  
4. A extensão agora aparece no local apropriado no Editor. Por exemplo, se você adicionar uma extensão de elemento de comportamento, ele aparecerá na lista de extensões disponíveis.  
  
#### <a name="hosting-environment"></a>Ambiente de hospedagem  
 Esta seção permite que você defina as configurações de instanciação para o ambiente de hospedagem de serviço.  
  
### <a name="creating-a-configuration-file-using-the-wizard"></a>Criando um arquivo de configuração usando o Assistente  
 Uma maneira de criar um novo arquivo de configuração é usar o Assistente para novo elemento de serviço. O assistente encontra os tipos de serviço instalado e outros elementos compatíveis com o WCF no computador, inclusive COM+ e diretórios virtuais hospedados na Web e carrega-os para tornar a criação da configuração de muito mais simplificada.  
  
#### <a name="creating-a-configuration-file"></a>Criando um arquivo de configuração  
  
1. Iniciar o Editor de configuração de serviço por meio de uma janela de comando para navegar até o local de instalação do WCF e, em seguida, digite `SvcConfigEditor.exe`.  
  
2. Dos **arquivo** menu, selecione **abra** e clique em **executável**, **COM+ Service**, ou **WebHosted Service**, dependendo do tipo de arquivo de configuração que você deseja criar.  
  
3. No **abrir** caixa de diálogo, navegue até o arquivo específico que você deseja criar um arquivo de configuração para e clique duas vezes nele.  
  
4. No **arquivo** , aponte para **Adicionar Novo Item** e clique em **serviço**. Abre o Assistente para novo elemento de serviço.  
  
5. Siga as etapas no Assistente para criar o novo serviço.  
  
> [!NOTE]
>  Se você quiser usar o NetPeerTcpBinding do arquivo de configuração gerado pelo assistente, você precisa adicionar um elemento de configuração de associação e modificar manualmente o `mode` atributo do seu `security` elemento como "None".  
  
## <a name="configuring-com"></a>Configuração de COM+  
 O Service Configuration Editor permite que você crie um novo arquivo de configuração para um aplicativo COM+ existente, ou editar uma configuração de COM+ existente. O **COM contrato** nó fica visível apenas quando o <`comContract`> seção existe no arquivo de configuração.  
  
### <a name="creating-a-new-com-configuration"></a>Criando uma nova configuração de COM+  
 Antes de criar uma nova configuração de COM+, certifique-se de que seu aplicativo COM+ está instalado nos serviços de componentes e registrado no Cache de Assembly Global (GAC).  
  
1. Selecione **arquivo** -> menu **integrar** -> **aplicativo COM+.** Esta operação fecha o atual arquivo aberto. Se existe é dados não salvos no arquivo atual, uma caixa de diálogo Salvar é exibida. O **do Assistente de integração COM+** , em seguida, é iniciado.  
  
2. Na primeira página, selecione o aplicativo COM+ da árvore. Se você não encontrar seu aplicativo COM+ na árvore, verifique se que ele é instalado em serviços de componentes e registrado no Cache de Assembly Global (GAC).  
  
3. Na próxima página, selecione qual método (s) que você deseja expor como serviços WCF. Todos os métodos com suporte no aplicativo COM+ são exibidos e selecionados por padrão.  
  
4. Escolha um método de hospedagem.  
  
5. Configure outras configurações de acordo com as guias no assistente.  
  
6. Editor de configuração de serviço utiliza ComSvcConfig.exe em segundo plano para gerar o arquivo de configuração. Depois de concluído, você pode exibir um resumo e sair do assistente. O arquivo de configuração gerado é aberto para que você pode editá-lo diretamente.  
  
### <a name="editing-an-existing-com-configuration"></a>Editando uma configuração de COM+ existente  
  
1. Selecione **arquivo** -> menu **abra** -> **COM+ Service**...  
  
2. Selecione Service COM+ que deseja editar na lista.  
  
3. Editar definições de configuração na **contratos COM** nó.  
  
    > [!NOTE]
    >  Também diretamente, você pode abrir e editar um arquivo de configuração que contém os contratos COM.  
  
## <a name="security"></a>Segurança  
 Um arquivo de configuração de serviço gerado pelo Editor de configuração não é garantido para ser seguro. Consulte a [segurança](../../../docs/framework/wcf/feature-details/security.md) documentação para saber como proteger seus serviços WCF.  
  
 Além disso, o Editor de configuração só pode ser usado para ler e gravar os elementos de configuração válidos do WCF. A ferramenta ignora elementos compatíveis com o esquema, definido pelo usuário. Ele também não tente remover esses elementos da configuração de arquivo ou a determinam seus efeitos sobre os elementos WCF conhecidos. É responsabilidade do usuário para determinar se esses elementos representam uma ameaça para o aplicativo ou o sistema.
