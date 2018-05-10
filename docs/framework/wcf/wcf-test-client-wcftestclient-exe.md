---
title: Cliente de Teste do WCF (WcfTestClient.exe)
ms.date: 03/30/2017
ms.assetid: d4302855-677f-4640-aa90-c5d785d72fb7
ms.openlocfilehash: 78be40268b46c4c85ee034db67d67ee0fbf2158f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="wcf-test-client-wcftestclientexe"></a>Cliente de Teste do WCF (WcfTestClient.exe)
Cliente de teste do Windows Communication Foundation (WCF) (WcfTestClient.exe) é uma ferramenta de interface gráfica do usuário que permite aos usuários inserir parâmetros de teste, enviar para o serviço de entrada e exibir a resposta que o serviço envia de volta. Ele fornece um serviço perfeito experiência quando combinado com o Host de serviço WCF em teste.  
  
 O cliente de teste do WCF (WcfTestClient.exe) geralmente podem ser encontrados no seguinte local: C:\Program Files (x86) \Microsoft Visual Studio\2017\Community\Common7\IDE - comunidade pode ser "Empresarial", "Professional" ou "Comunidade", dependendo de qual nível do Visual Studio está instalado.
  
## <a name="scenarios-for-using-test-client"></a>Cenários para uso do Cliente de Teste  
 As seções a seguir discutem os cenários mais comuns em que você pode usar o cliente de teste do WCF para simplificar o processo de desenvolvimento.  
  
### <a name="inside-visual-studio"></a>No Visual Studio  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-a-single-service"></a>O Host de Serviço WCF começa o Cliente de Teste do WCF com o um único serviço  
 Depois de criar um novo projeto de serviço do WCF e pressione F5 para iniciar o depurador, o Host de serviço do WCF começa a hospedar o serviço em seu projeto. Em seguida, o cliente de teste do WCF é aberto e exibe uma lista de pontos de extremidade de serviço definidos no arquivo de configuração. Você pode testar os parâmetros e chamar o serviço, e repetir esse processo para testar e validar continuamente o serviço.  
  
#### <a name="wcf-service-host-starts-wcf-test-client-with-multiple-services"></a>O Host de Serviço WCF começa o Cliente de Teste do WCF com vários serviços  
 Você também pode usar o cliente de teste do WCF para ajudar a depurar um projeto de serviço que contém vários serviços. Quando o cliente de teste do WCF é aberto, ele automaticamente itera a lista de serviços em seu projeto e abre-os para teste.  
  
### <a name="outside-visual-studio"></a>Fora do Visual Studio  
 Você também pode invocar o cliente de teste do WCF (WcfTestClient.exe) fora do Visual Studio para testar um serviço arbitrário na Internet. Para localizar a ferramenta, vá para o seguinte local:  
  
 C:\Arquivos de Programas\Microsoft Visual Studio 9.0\Common7\IDE\  
  
 Para usar a ferramenta, clique duas vezes no nome do arquivo para abri-lo neste local ou inicie-a em uma linha de comando.  
  
 Cliente de teste do WCF tem um número arbitrário de URIs como argumentos de linha de comando.  Estes são os URIs de serviços que podem ser testados.  
  
 `wcfTestClient.exe URI1 URI2 …`  
  
 Depois que a janela do cliente de teste do WCF é aberta, clique em **arquivo**->**Adicionar serviço**e digite o endereço do ponto de extremidade do serviço que deseja abrir.  
  
## <a name="wcf-test-client-user-interface"></a>Interface do usuário do Cliente de Teste do WCF  
 Você pode usar o cliente de teste do WCF com um único serviço ou vários serviços.  
  
### <a name="service-operations"></a>Operações de serviço  
 O painel esquerdo da janela principal do cliente de teste do WCF lista todos os serviços disponíveis, junto com seus respectivos pontos de extremidade e operações.  
  
 Clicando duas vezes em uma operação, você pode exibir seu conteúdo no painel direito em um nova guia com o nome da operação.  
  
 O painel esquerdo também lista arquivos de configuração de cliente. Clique duas vezes em alguns dos itens para exibir o conteúdo do arquivo em uma nova janela com guias no painel direito.  
  
### <a name="entering-test-parameters"></a>Inserindo parâmetros de teste  
 Para exibir os parâmetros de teste, clique duas vezes em uma operação para abri-la no painel direito. Os parâmetros são mostrados na **formatados** exibição por padrão, e você pode inserir valores arbitrários para os parâmetros testar o serviço.  
  
 Para exibir o XML da mensagem, clique em **XML**. Para enviá-los para o serviço, clique em **Invoke**.  
  
 Para um parâmetro de conjunto de dados, clique no **...** próximo ao **editar...** para editá-lo em uma nova janela mostrando a grade de dados. Observe a aparência do **conjunto de dados de cópia** e **colar DataSet** botões. Se o esquema do objeto DataSet for desconhecido na primeira edição, o DataGrid estará vazio. Você precisa colar um objeto DataSet com o mesmo esquema no objeto atual no DataGrid. Observe que você precisa copiar o esquema de algum outro lugar antes da operação de colagem. Você também pode copiar um objeto de conjunto de dados para uso futuro clicando o **conjunto de dados de cópia** botão.  
  
 A resposta do serviço aparece abaixo dos parâmetros de teste.  
  
> [!NOTE]
>  Se o valor de retorno esperado for uma cadeia de caracteres, o resultado será exibido como uma cadeia de caracteres entre aspas, mesmo que a entrada não tenha sido fornecida entre aspas.  
  
 Se você tiver definido uma operação específica como unidirecional quando criou o contrato do serviço, nenhuma resposta do serviço será exibida. Assim que a mensagem for enfileirada para entrega, uma caixa de diálogo pop-up será exibida notificando que a mensagem foi enviada com êxito.  
  
### <a name="session-support"></a>Suporte de sessão  
 O **iniciar um novo proxy** caixa de seleção na guia de uma operação de serviço permite que você alterne o suporte de sessão. Por padrão, essa caixa está desmarcada.  
  
 Quando você inserir parâmetros de teste para uma operação específica (ou outra operação no mesmo ponto de extremidade de serviço) e clique em **Invoke** várias vezes com a caixa de seleção desmarcada, essas operações compartilham um proxy e o status do serviço é persistente em várias operações.  
  
 Se o **iniciar um novo proxy** caixa de seleção estiver marcada, um novo proxy é iniciado para cada **Invoke**, o cenário de sessão anterior é encerrado e o status do serviço é redefinido.  
  
### <a name="editing-client-configuration"></a>Editando a configuração do cliente  
 O painel esquerdo da janela principal do cliente de teste do WCF lista os arquivos de configuração do cliente. Clique duas vezes em alguns dos itens para exibir o conteúdo do arquivo no painel direito.  
  
#### <a name="edit-with-service-configuration-editor"></a>Editar com o Service Configuration Editor  
 Clique com botão direito **arquivo de configuração** no painel esquerdo e selecione o menu de contexto **Editar com SvcConfigEditor**. O Service Configuration Editor é iniciado com o conteúdo de configuração do cliente. Você pode editar a configuração e salvá-la na ferramenta.  
  
 Depois de salvar o arquivo no Editor de configuração de serviço, o cliente de teste do WCF exibe uma mensagem de aviso informando que o arquivo foi modificado fora e pergunta se você deseja recarregá-lo.  
  
 Se você selecionar **Sim**, o conteúdo de configuração na guia "Client.dll. config" reflete as alterações feitas no editor.  
  
 Se você selecionar **não**, o conteúdo de configuração na guia "Client.dll. config" permanece inalterado e o conteúdo modificado é salvo automaticamente para o arquivo de origem.  
  
#### <a name="restore-to-default-configuration"></a>Restaurar para a configuração padrão  
 Se você quiser cancelar todas as alterações e restaurar a configuração do cliente padrão, clique no **arquivo de configuração** no painel esquerdo e selecione o menu de contexto **restaurar para a configuração padrão**. O valor de configuração padrão é carregado e o conteúdo no guia de "Client.dll. config" será restaurado.  
  
#### <a name="validate-changes"></a>Validar alterações  
 Ao salvar alterações estão sendo carregadas no cliente de teste do WCF, a configuração é verificada para validade com base no esquema do WCF. Se forem encontrados erros, uma caixa de diálogo será exibida para mostrar os detalhes do erro.  
  
 Durante a geração de proxy, compilando binários ou invocação de serviço, os itens de menu que dão suporte à edição (ou seja, "Editar...", "Restore..." e assim por diante) estão desabilitadas. Invocação de serviço também será desabilitada quando o carregamento de configuração atualizada para o cliente de teste do WCF.  
  
#### <a name="persist-client-configuration"></a>Persistir a configuração do cliente  
 O **ferramentas**->**opções**->**configuração do cliente** guia contém um **sempre Gerar configuração ao iniciar Serviços** opção, que é habilitada por padrão. Esta opção especifica que sempre que o cliente de teste do WCF carrega um serviço, ele gera novamente um arquivo de configuração com base no contrato de serviço mais recente e arquivos de App. config do serviço.  
  
 Se você editou a configuração do cliente para o serviço WCF e sempre usar esse arquivo atualizado para depurar seu serviço, você pode desmarcar a **regenerar** opção. Ao fazer isso, mesmo quando você atualizar o serviço e reabrir o cliente de teste do WCF, o arquivo Client.dll. config é aquele que você atualizou anteriormente, em vez de regenerada uma baseada no serviço atualizado.  
  
 No entanto, talvez você precise editar o arquivo de configuração para torná-lo consistente com o proxy regenerado. Se o proxy e o arquivo de configuração regenerados forem incompatíveis devido a um serviço atualizado, ocorrerão erros quando o serviço for chamado.  
  
> [!CAUTION]
>  Se você tiver modificado o arquivo de configuração do cliente e o selecionar para reutilização no futuro, poderá localizar o arquivo no seguinte local:  
>   
>  \Documents and Settings\\projetos de cliente \My Documents\Test [conta de usuário].  
>   
>  Todas as informações de credenciais atualizadas armazenadas no arquivo de configuração do cliente são protegidas pela ACL (lista de controle de acesso) dessa pasta.  
  
### <a name="adding-removing-and-refreshing-services"></a>Adicionando, removendo e atualizando serviços  
  
#### <a name="add-service"></a>Adicionar serviço  
 Clique em **arquivo**->**Adicionar serviço** para adicionar um serviço de cliente de teste do WCF. Em seguida, é necessário digitar o URI (endereço do ponto de extremidade) do serviço a ser adicionado. O endereço do serviço pode ser um endereço MEX ou um endereço WSDL.  
  
 Você também pode encontrar uma lista de pontos de extremidade de 10 serviços adicionado recentemente no **serviços recente** submenu. Se você selecionar um deles, o serviço especificado é adicionado ao cliente de teste do WCF.  
  
 Você pode também clique a raiz da árvore de serviço **meus projetos de serviço**e selecione **Adicionar serviço** para alcançar o mesmo resultado.  
  
 Durante a geração do proxy, da compilação binária ou da chamada do serviço, os itens de menu que dão suporte à edição de um serviço estão desabilitados. A chamada de serviço também está desabilitada.  
  
#### <a name="remove-service"></a>Remover serviço  
 Clique com botão direito a raiz do serviço do serviço a ser removido e selecione **remover serviço** para remover um serviço de cliente de teste do WCF.  
  
 Durante a geração do proxy, da compilação binária ou da chamada do serviço, os itens de menu que dão suporte à remoção de um serviço estão desabilitados. A chamada de serviço também está desabilitada.  
  
#### <a name="refresh-service"></a>Atualizar serviço  
 Se uma alteração for feita para o serviço enquanto o cliente de teste do WCF está em execução e você deseja garantir que a implementação do cliente de teste do WCF para esse serviço é atualizada, clique com botão direito a raiz do serviço do serviço e selecione **atualizar serviço**. Observe que depois da atualização, o status do serviço é redefinido.  
  
 Durante a geração do proxy, da compilação binária ou da chamada do serviço, os itens de menu que dão suporte à atualização de um serviço estão desabilitados. A chamada de serviço também está desabilitada.  
  
## <a name="location-of-files-generated-by-the-test-client"></a>Local dos arquivos gerados pelo Cliente de Teste  
 Por padrão, o cliente de teste do WCF armazena gerado arquivos de código e configuração do cliente na pasta "%appdata%\Local\temp\Test projetos de cliente". Essa pasta é excluída após a saída do cliente de teste do WCF. Se um arquivo de configuração é modificado no cliente de teste do WCF e o **sempre Gerar configuração quando iniciar serviços** opção estiver desabilitada, o arquivo modificado é copiado para a pasta de "Configuração armazenado em cache" em "Meu Documents\Test projetos de cliente Projetos de cliente Documents\Test"com um arquivo de XML do mapeamento (metadados-endereço-para-nome de arquivo) como um índice.  
  
 Você também pode iniciar o cliente de teste do WCF em uma linha de comando, use o `/ProjectPath` para especificar um novo caminho desejado para armazenar os arquivos gerados ou usar o `/RestoreProjectPath` switch para restaurar o local padrão. A sintaxe é a seguinte:  
  
 `wcfTestClient.exe /ProjectPath [desired location]`  
  
 A execução desse comando não abre o cliente de teste do WCF. Apenas o local da pasta é alterado. Você pode executar esse comando se o cliente de teste do WCF em execução ou não. O novo local é aplicado quando o cliente de teste do WCF é reiniciado. As informações de local podem ser salvos no registro ou no arquivo WcfTestClient.exe.option na pasta "%appdata%\Local\temp\Test projetos de cliente".  
  
## <a name="features-supported-by-wcf-test-client"></a>Recursos suportados pelo Cliente de Teste do WCF  
 A seguir está uma lista de recursos com suporte pelo cliente de teste do WCF:  
  
-   Chamada de serviço: solicitação/resposta e mensagem unidirecional.  
  
-   Associações: todas as associações suportadas por Svcutil.exe.  
  
-   Sessão de controle.  
  
-   Contrato de mensagens.  
  
-   Serialização XML.  
  
 A seguir está uma lista de recursos sem suporte pelo cliente de teste do WCF:  
  
-   Tipos: <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlNode>, tipos que implementam a interface de <xref:System.Xml.Serialization.IXmlSerializable>, incluindo o atributo <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> relacionado e os tipos <xref:System.Xml.Linq.XDocument> e <xref:System.Xml.Linq.XElement> e o tipo <xref:System.Data.DataTable> do ADO.NET.  
  
-   Contrato dúplex.  
  
-   Transação.  
  
-   Segurança: [!INCLUDE[infocard](../../../includes/infocard-md.md)], certificado e nome de usuário/senha.  
  
-   Associações: WSFederationbinding, algumas associações de contexto e associação HTTPS, WebHttpbinding (suporte a mensagem de resposta de Json).  
  
## <a name="closing-wcf-test-client"></a>Fechando o Cliente de Teste do WCF  
 Você pode fechar o cliente de teste do WCF das seguintes maneiras:  
  
-   Sobre o **arquivo** menu, clique em **saída**. Como alternativa, na janela principal do cliente de teste do WCF, clique em **fechar**. Essas ações também desligar o Host de automático do serviço WCF tanto interromper o processo de depuração do Visual Studio se o cliente de teste do WCF foi iniciado pelo Visual Studio.  
  
-   Clique com botão direito do **Host de serviço WCF** ícone na área de notificação e, em seguida, clique **sair.** Isso desliga o Host de automático do serviço WCF e o cliente de teste do WCF e interrompe o processo de depuração do Visual Studio.  
  
## <a name="see-also"></a>Consulte também  
 [Host de serviço do WCF (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
