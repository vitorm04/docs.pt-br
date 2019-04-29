---
title: Cliente de Teste do WCF (WcfTestClient.exe)
ms.date: 03/30/2017
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
ms.openlocfilehash: cd6f0d7a98ca5bc5f6bee45ad296341a5b91b2a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791190"
---
# <a name="wcf-test-client-wcftestclientexe"></a>Cliente de Teste do WCF (WcfTestClient.exe)
Cliente de teste do Windows Communication Foundation (WCF) (WcfTestClient.exe) é uma ferramenta de GUI que permite aos usuários inserir parâmetros de teste, enviem essa entrada para o serviço e exibir a resposta que o serviço envia de volta. Ele fornece um serviço perfeito experiência quando combinado com o Host de serviço WCF em teste.  
  
 O cliente de teste do WCF (WcfTestClient.exe) geralmente podem ser encontrados no seguinte local: `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` – a comunidade pode ser um dos "Enterprise", "Professional" ou "Community", dependendo de qual nível do Visual Studio está instalado.
  
## <a name="scenarios-for-using-test-client"></a>Cenários para uso do Cliente de Teste  
 As seções a seguir discutem os cenários mais comuns em que você pode usar o cliente de teste do WCF para simplificar o processo de desenvolvimento.  
  
### <a name="inside-visual-studio"></a>No Visual Studio  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a>O Host de Serviço WCF começa o Cliente de Teste do WCF com o um único serviço  
 Depois de criar um novo projeto de serviço do WCF e pressione F5 para iniciar o depurador, o Host de serviço WCF começa a hospedar o serviço em seu projeto. Em seguida, o cliente de teste do WCF é aberta e exibe uma lista de pontos de extremidade de serviço definidos no arquivo de configuração. Você pode testar os parâmetros e chamar o serviço, e repetir esse processo para testar e validar continuamente o serviço.  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a>O Host de Serviço WCF começa o Cliente de Teste do WCF com vários serviços  
 Você também pode usar o cliente de teste do WCF para ajudar a depurar um projeto de serviço que contém vários serviços. Quando o cliente de teste do WCF é aberto, ele automaticamente itera a lista de serviços em seu projeto e abre-os para teste.  
  
### <a name="outside-visual-studio"></a>Fora do Visual Studio  
 Você também pode chamar o cliente de teste do WCF (WcfTestClient.exe) fora do Visual Studio para testar um serviço arbitrário na Internet. Para localizar a ferramenta, vá para o seguinte local:  
  
 `C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE` (onde comunidade pode ser um "Enterprise", "Professional" ou "Community", dependendo de qual nível do Visual Studio está instalado no computador)
  
 Para usar a ferramenta, clique duas vezes no nome do arquivo para abri-lo neste local ou inicie-a em uma linha de comando.  
  
 Cliente de teste do WCF usa um número arbitrário de URIs como argumentos de linha de comando.  Estes são os URIs de serviços que podem ser testados.  
  
 `wcfTestClient.exe URI1 URI2 …`  
  
 Depois que a janela de cliente de teste do WCF é aberta, clique em **arquivo**->**Adicionar serviço**e digite o endereço do ponto de extremidade do serviço que você deseja abrir.  
  
## <a name="wcf-test-client-user-interface"></a>Interface do usuário do Cliente de Teste do WCF  
 Você pode usar o cliente de teste do WCF com um único serviço ou com vários serviços.  
  
### <a name="service-operations"></a>Operações de serviço  
 O painel esquerdo da janela principal do cliente de teste do WCF lista todos os serviços disponíveis, juntamente com seus respectivos pontos de extremidade e operações.  
  
 Clicando duas vezes em uma operação, você pode exibir seu conteúdo no painel direito em um nova guia com o nome da operação.  
  
 O painel esquerdo também lista arquivos de configuração de cliente. Clique duas vezes em alguns dos itens para exibir o conteúdo do arquivo em uma nova janela com guias no painel direito.  
  
### <a name="entering-test-parameters"></a>Inserindo parâmetros de teste  
 Para exibir os parâmetros de teste, clique duas vezes em uma operação para abri-la no painel direito. Os parâmetros são mostrados na **formatado** exibição por padrão, e você pode inserir valores arbitrários para os parâmetros testar o serviço.  
  
 Para exibir o XML da mensagem, clique em **XML**. Para enviá-los para o serviço, clique em **Invoke**.  
  
 Para um parâmetro de conjunto de dados, clique no **...** lado **editar...** para editá-lo em uma nova janela que mostra o DataGrid. Observe a aparência do **conjunto de dados de cópia** e **colar DataSet** botões. Se o esquema do objeto DataSet for desconhecido na primeira edição, o DataGrid estará vazio. Você precisa colar um objeto DataSet com o mesmo esquema no objeto atual no DataGrid. Observe que você precisa copiar o esquema de algum outro lugar antes da operação de colagem. Você também pode copiar um objeto de conjunto de dados para uso futuro clicando o **conjunto de dados de cópia** botão.  
  
 A resposta do serviço aparece abaixo dos parâmetros de teste.  
  
> [!NOTE]
>  Se o valor de retorno esperado for uma cadeia de caracteres, o resultado será exibido como uma cadeia de caracteres entre aspas, mesmo que a entrada não tenha sido fornecida entre aspas.  
  
 Se você tiver definido uma operação específica como unidirecional quando criou o contrato do serviço, nenhuma resposta do serviço será exibida. Assim que a mensagem for enfileirada para entrega, uma caixa de diálogo pop-up será exibida notificando que a mensagem foi enviada com êxito.  
  
### <a name="session-support"></a>Suporte de sessão  
 O **iniciar um novo proxy** caixa de seleção na guia da operação do serviço permite que você alterne o suporte de sessão. Por padrão, essa caixa está desmarcada.  
  
 Quando você insere parâmetros de teste para uma operação específica (ou outra operação no mesmo ponto de extremidade de serviço) e clique em **Invoke** várias vezes com a caixa de seleção desmarcada, essas operações compartilham um proxy e o status do serviço é persistido em várias operações.  
  
 Se o **iniciar um novo proxy** caixa de seleção estiver marcada, um novo proxy será iniciado para cada **Invoke**, o cenário de sessão anterior é encerrado e o status do serviço é redefinido.  
  
### <a name="editing-client-configuration"></a>Editando a configuração do cliente  
 O painel esquerdo da janela principal do cliente de teste do WCF lista arquivos de configuração do cliente. Clique duas vezes em alguns dos itens para exibir o conteúdo do arquivo no painel direito.  
  
#### <a name="edit-with-service-configuration-editor"></a>Editar com o Service Configuration Editor  
 Clique com botão direito **arquivo de configuração** no painel esquerdo e selecione o menu de contexto **Editar com SvcConfigEditor**. O Service Configuration Editor é iniciado com o conteúdo de configuração do cliente. Você pode editar a configuração e salvá-la na ferramenta.  
  
 Depois de salvar o arquivo no Editor de configuração de serviço, o cliente de teste do WCF exibe uma mensagem de aviso para informar que o arquivo foi modificado fora e pergunta se você deseja recarregá-lo.  
  
 Se você selecionar **Sim**, o conteúdo da configuração na guia "Client" reflete as alterações feitas no editor.  
  
 Se você selecionar **não**, o conteúdo da configuração na guia "Client" permanece inalterado e o conteúdo modificado é salvo automaticamente ao arquivo de origem.  
  
#### <a name="restore-to-default-configuration"></a>Restaurar para a configuração padrão  
 Se você quiser cancelar todas as alterações e restaurar a configuração do cliente padrão, clique com botão direito **arquivo de configuração** no painel esquerdo e selecione o menu de contexto **restaurar para a configuração padrão**. O valor de configuração padrão é carregado e o conteúdo na guia "Client" é restaurado.  
  
#### <a name="validate-changes"></a>Validar alterações  
 Quando alterações salvas estiverem sendo carregadas no cliente de teste do WCF, a configuração é verificada quanto à validade com relação ao esquema do WCF. Se forem encontrados erros, uma caixa de diálogo será exibida para mostrar os detalhes do erro.  
  
 Durante a geração de proxy, da compilação binária ou invocação de serviço, os itens de menu que dão suporte à edição (isto é, "Editar...", "Restaurar..." e assim por diante) estão desabilitados. Invocação de serviço também é desabilitada ao carregar a configuração atualizada ao cliente de teste do WCF.  
  
#### <a name="persist-client-configuration"></a>Persistir a configuração do cliente  
 O **ferramentas**->**opções**->**configuração do cliente** guia contém um **sempre regenerar configuração ao iniciar Serviços** opção, que é habilitada por padrão. Esta opção especifica que sempre que o cliente de teste do WCF carrega um serviço, ele gera novamente um arquivo de configuração com base no contrato de serviço mais recente e nos arquivos de App. config do serviço.  
  
 Se você editou a configuração do cliente para seu serviço WCF e desejar sempre usar esse arquivo atualizado para depurar seu serviço, você pode desmarcar a **regenerar** opção. Ao fazer isso, mesmo quando você atualiza o serviço e reabrir o cliente de teste do WCF, o arquivo regenerado é aquele que você atualizou anteriormente em vez de um com base no serviço atualizado.  
  
 No entanto, talvez você precise editar o arquivo de configuração para torná-lo consistente com o proxy regenerado. Se o proxy e o arquivo de configuração regenerados forem incompatíveis devido a um serviço atualizado, ocorrerão erros quando o serviço for chamado.  
  
> [!CAUTION]
>  Se você tiver modificado o arquivo de configuração do cliente e o selecionar para reutilização no futuro, poderá localizar o arquivo no seguinte local:  
>   
>  \Documents and Settings\\[conta de usuário] \My Documents\Test Client Projects.  
>   
>  Todas as informações de credenciais atualizadas armazenadas no arquivo de configuração do cliente são protegidas pela ACL (lista de controle de acesso) dessa pasta.  
  
### <a name="adding-removing-and-refreshing-services"></a>Adicionando, removendo e atualizando serviços  
  
#### <a name="add-service"></a>Adicionar serviço  
 Clique em **arquivo**->**Adicionar serviço** para adicionar um serviço ao cliente de teste do WCF. Em seguida, é necessário digitar o URI (endereço do ponto de extremidade) do serviço a ser adicionado. O endereço do serviço pode ser um endereço MEX ou um endereço WSDL.  
  
 Você também pode encontrar uma lista dos pontos de extremidade 10 serviços adicionados recentemente a **serviços recentes** submenu. Se você selecionar um deles, o serviço especificado é adicionado ao cliente de teste do WCF.  
  
 Pode também clicar duas vezes a raiz da árvore de serviço **meus projetos de serviço**e selecione **Adicionar serviço** para alcançar o mesmo resultado.  
  
 Durante a geração do proxy, da compilação binária ou da chamada do serviço, os itens de menu que dão suporte à edição de um serviço estão desabilitados. A chamada de serviço também está desabilitada.  
  
#### <a name="remove-service"></a>Remover serviço  
 Clique com botão direito do serviço a ser removido e, em seguida, selecione a raiz do serviço **remover serviço** para remover um serviço de cliente de teste do WCF.  
  
 Durante a geração do proxy, da compilação binária ou da chamada do serviço, os itens de menu que dão suporte à remoção de um serviço estão desabilitados. A chamada de serviço também está desabilitada.  
  
#### <a name="refresh-service"></a>Atualizar serviço  
 Se uma alteração for feita para o serviço enquanto o cliente de teste do WCF está em execução e você deseja garantir que a implementação de cliente de teste do WCF para o serviço é atualizada, clique com botão direito na raiz do serviço e selecione **Refresh serviço**. Observe que depois da atualização, o status do serviço é redefinido.  
  
 Durante a geração do proxy, da compilação binária ou da chamada do serviço, os itens de menu que dão suporte à atualização de um serviço estão desabilitados. A chamada de serviço também está desabilitada.  
  
## <a name="location-of-files-generated-by-the-test-client"></a>Local dos arquivos gerados pelo Cliente de Teste  
 Por padrão, os repositórios de cliente de teste do WCF gerado os arquivos de código e a configuração do cliente na pasta "%appdata%\Local\temp\Test Client Projects". Essa pasta é excluída após o encerramento de cliente de teste do WCF. Se um arquivo de configuração é modificado no cliente de teste do WCF e o **sempre regenerar configuração ao iniciar serviços** opção está desabilitada, o arquivo modificado será copiado para a pasta "CachedConfig" em "Meus documentos\test Client Projects" com um arquivo XML (metadados-endereço-para-file-name) de mapeamento como um índice.  
  
 Você também pode iniciar o cliente de teste do WCF em uma linha de comando, use o `/ProjectPath` alternar para especificar um novo caminho desejado para armazenar os arquivos gerados ou usar o `/RestoreProjectPath` switch para restaurar o local padrão. A sintaxe é a seguinte:  
  
 `wcfTestClient.exe /ProjectPath [desired location]`  
  
 A execução desse comando não abre o cliente de teste do WCF. Apenas o local da pasta é alterado. Você pode executar esse comando se o cliente de teste do WCF em execução ou não. O novo local é aplicado quando o cliente de teste do WCF é reiniciado. As informações de local podem ser salvos no registro ou no arquivo WcfTestClient na pasta "%appdata%\Local\temp\Test Client Projects".  
  
## <a name="features-supported-by-wcf-test-client"></a>Recursos suportados pelo Cliente de Teste do WCF  
 A seguir está uma lista dos recursos suportados pelo cliente de teste do WCF:  
  
- Invocação de serviço: Solicitação/resposta e mensagem unidirecional.  
  
- Associações: todas as associações suportadas por Svcutil.exe.  
  
- Sessão de controle.  
  
- Contrato de mensagens.  
  
- Serialização XML.  
  
 A seguir está uma lista de recursos sem suporte pelo cliente de teste do WCF:  
  
- Tipos: <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlNode>, tipos que implementam a interface de <xref:System.Xml.Serialization.IXmlSerializable>, incluindo o atributo <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> relacionado e os tipos <xref:System.Xml.Linq.XDocument> e <xref:System.Xml.Linq.XElement> e o tipo <xref:System.Data.DataTable> do ADO.NET.  
  
- Contrato dúplex.  
  
- Transação.  
  
- Segurança: [!INCLUDE[infocard](../../../includes/infocard-md.md)], certificado e nome de usuário/senha.  
  
- Associações: WSFederationbinding, quaisquer associações de contexto e associação de Https, WebHttpbinding (suporte de mensagem de resposta Json).  
  
## <a name="closing-wcf-test-client"></a>Fechando o Cliente de Teste do WCF  
 Você pode fechar o cliente de teste do WCF das seguintes maneiras:  
  
- Sobre o **arquivo** menu, clique em **sair**. Como alternativa, na janela principal do cliente de teste do WCF, clique em **fechar**. Essas ações também desligar a hospedagem de automática do serviço WCF tanto interromper o processo de depuração do Visual Studio, se o cliente de teste do WCF foi iniciado pelo Visual Studio.  
  
- Clique com botão direito do **Host de serviço WCF** ícone na área de notificação e depois clique em **sair.** Isso desliga a hospedagem de automática do serviço WCF e o cliente de teste do WCF e interrompe o processo de depuração do Visual Studio.  
  
## <a name="see-also"></a>Consulte também

- [Host de serviço do WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
