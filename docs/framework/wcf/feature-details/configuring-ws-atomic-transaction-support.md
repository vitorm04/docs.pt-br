---
title: Configurando suporte de transações de WS-Atomic
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF], configuring WS-Atomic Transaction
ms.assetid: cb9f1c9c-1439-4172-b9bc-b01c3e09ac48
ms.openlocfilehash: 4d0e0a1bea32fe3be896b80e77de34e04cd9f2f4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396327"
---
# <a name="configuring-ws-atomic-transaction-support"></a>Configurando suporte de transações de WS-Atomic
Este tópico descreve como você pode configurar o suporte de WS-AtomicTransaction (WS-AT) usando o utilitário de configuração do WS-AT.  
  
## <a name="using-the-ws-at-configuration-utility"></a>Usando o utilitário de configuração WS-AT  
 O utilitário de configuração do WS-AT (wsatConfig.exe) é usado para definir as configurações de WS-AT. Para habilitar o serviço de protocolo WS-AT, você deve usar o utilitário de configuração para configurar a porta HTTPS para WS-AT, associar um certificado X.509 para a porta HTTPS e configurar certificados de parceiro autorizado, especificando nomes de entidade do certificado ou impressões digitais. O utilitário de configuração também permite que você selecione o modo de rastreamento e saída do conjunto padrão e máximo entrada tempos limite de transação.  
  
 Você pode acessar a funcionalidade desta ferramenta usando um snap-in de página de propriedade de Console de gerenciamento Microsoft (MMC) no console de gerenciamento de serviços de componentes ou de uma janela de linha de comando. Configurar o suporte de WS-AT no computador local por meio da janela de linha de comando; Defina configurações em computadores locais e remotos usando o snap-in do MMC.  
  
 A janela de linha de comando pode ser acessada no local de instalação do SDK do Windows "%WINDIR%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation".  
  
 Para obter mais informações sobre a ferramenta de linha de comando, consulte [WS-AtomicTransaction utilitário de configuração (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md).  
  
 Se você estiver executando [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ou [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], você pode acessar o snap-in do MMC, navegando até **serviços de componente/ferramentas de controle do painel/administrativos**, com o botão direito **meu computador**, e selecionando **propriedades**. Isso é o mesmo local onde você pode configurar o Microsoft Distributed Transaction coordenador (MSDTC). As opções disponíveis para configuração estão agrupadas sob o **WS-AT** guia. Se você estiver executando o Windows Vista ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)], o snap-in do MMC pode ser encontrado clicando o **começar** botão e inserindo `dcomcnfg.exe` no **pesquisa** caixa. Quando o MMC for aberto, navegue até a **Meus Computer\Distributed transação Coordinator\Local DTC** nó, clique com botão direito e selecione **propriedades**. As opções disponíveis para configuração estão agrupadas sob o **WS-AT** guia.  
  
 Para obter mais informações sobre o snap-in, consulte a [Snap-in MMC de configuração WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md).  
  
 Para habilitar a interface do usuário da ferramenta, você deve primeiro registrar o arquivo WsatUI.dll, localizado no seguinte caminho  
  
 %ProgramFiles%\Microsoft SDKs\Windows\v6.0\Bin  
  
 Para registrar o produto, execute o seguinte comando em uma janela do Prompt de comando:  
  
 `regasm.exe /codebase WsatUI.dll`  
  
## <a name="enabling-ws-at"></a>Habilitando WS-AT  
 Para habilitar o serviço de protocolo WS-AT dentro do MSDTC usando a porta 443 e um certificado X.509 com uma chave privada que foi instalada no repositório do computador local, use a ferramenta de wsatConfig.exe com o comando a seguir.  
  
 `WsatConfig.exe –network:enable –port:8443 –endpointCert:<machine|"Issuer\SubjectName"> -accountsCerts:<thumbprint|"Issuer\SubjectName"> -restart`  
  
 Substitua os respectivos parâmetros com valores relevantes para seu ambiente.  
  
 Para desabilitar o serviço de protocolo WS-AT dentro do MSDTC, use a ferramenta de wsatConfig.exe com o comando a seguir.  
  
 `WsatConfig.exe –network:disable -restart`  
  
## <a name="configuring-trust-between-two-machines"></a>Configurar confiança entre dois computadores  
 O serviço de protocolo WS-AT exige que o administrador explicitamente Autorizar contas individuais para participar de transações distribuídas. Se você for um administrador para duas máquinas, você pode configurar ambas as máquinas para estabelecer uma relação de confiança mútua trocando o conjunto certo de certificados entre as máquinas, instalá-los em armazenamentos de certificados apropriados e usando o ferramenta de wsatConfig.exe para adicionar o certificado de cada máquina dos outros lista de certificados de participantes autorizados. Essa etapa é necessária executar transações distribuídas entre dois computadores que usam WS-AT.  
  
 No exemplo a seguir descreve as etapas para estabelecer a confiança entre dois computadores, A e B.  
  
### <a name="creating-and-exporting-certificates"></a>Criando e exportando certificados  
 Este procedimento requer o snap-in MMC de certificados. O snap-in pode ser acessado abrindo o menu Iniciar/Executar, digite "mmc" na caixa de entrada e pressionar Okey. Em seguida, nos **Console1** janela, navegue até **arquivo/adicionar ou remover** Snap-in, clique em Adicionar e escolha **certificados** do **autônomos disponíveis Snap-ins** lista. Por fim, selecione **conta de computador** para gerenciar e clique em **Okey**. O **certificados** nó aparece no console do snap-in.  
  
 Você já deve ter os certificados necessários para estabelecer a confiança. Para saber como criar e instalar novos certificados antes das etapas a seguir, consulte [como: criar e instalar certificados de cliente temporários no WCF durante o desenvolvimento](https://go.microsoft.com/fwlink/?LinkId=158925).  
  
1.  No computador A usando o snap-in, a importação de certificados do MMC o certificado existente (certA) no LocalMachine\MY (nó pessoal) e store LocalMachine\ROOT (nó de autoridade de certificação raiz confiável). Para importar um certificado para um nó específico, clique com botão direito no nó e escolha **todas as tarefas/importação**.  
  
2.  No computador B, usando o snap-in do MMC de certificados, criar ou obter um certificado certB com uma chave privada e importá-lo para o LocalMachine\MY (nó pessoal) e o armazenamento de LocalMachine\ROOT (nó de autoridade de certificação raiz confiável).  
  
3.  Exporte a chave pública de certA para um arquivo se isso não já foi feito.  
  
4.  Exporte chave pública do certB para um arquivo, se isso não já foi feito.  
  
### <a name="establishing-mutual-trust-between-machines"></a>Estabelecendo a confiança mútua entre máquinas  
  
1.  No computador A, importe a representação de arquivo de certB nos armazenamentos de LocalMachine\MY e LocalMachine\ROOT. Isso declara nessa máquina um certB de relações de confiança para se comunicar com ele.  
  
2.  No computador B, importe o arquivo do certA para os repositórios de LocalMachine\MY e LocalMachine\ROOT. Isso implica na máquina B certA de relações de confiança para se comunicar com ele.  
  
 Depois de concluir essas etapas, a relação de confiança é estabelecida entre as duas máquinas, e eles podem ser configurados para se comunicar entre si usando WS-AT.  
  
### <a name="configuring-msdtc-to-use-certificates"></a>Configurar o MSDTC para usar certificados  
 Desde que o serviço de protocolo WS-AT atua como um cliente e um servidor, ele deve escutar conexões de entrada tanto iniciar conexões de saída. Portanto, você precisa configurar o MSDTC para que ele saiba qual certificado usar ao se comunicar com parceiros externos e quais certificados para autorizar ao aceitar a entrada de comunicação.  
  
 Você pode configurar isso usando o snap-in do MMC WS-AT. Para obter mais informações sobre essa ferramenta, consulte o [Snap-in MMC de configuração WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) tópico. As etapas a seguir descrevem como estabelecer a relação de confiança entre dois computadores executando o MSDTC.  
  
1.  Defina configurações de máquina do. Para "Certificado do ponto de extremidade", selecione certA. Por "Certificados autorizado", selecione o certB.  
  
2.  Defina configurações do computador B. Para "Certificado do ponto de extremidade", selecione certB. Por "Certificados autorizado", selecione o certA.  
  
> [!NOTE]
>  Quando um computador envia uma mensagem ao outro computador, o remetente tenta verificar o nome da entidade do certificado do destinatário e o nome da máquina do destinatário correspondem. Se eles não corresponderem, falha de verificação do certificado e as duas máquinas não podem se comunicar.  
>   
>  Para um computador ingressado em um domínio, o nome é o nome de domínio totalmente qualificado. Por padrão, o nome de uma máquina em um grupo de trabalho é o nome do computador NetBIOS. No entanto, o nome também pode incluir um sufixo do sistema de nome de domínio (DNS), se um estiver presente para a conexão que está sendo usado entre os dois computadores.  
>   
>  Se o nome da máquina for alterado, por exemplo, quando um computador de grupo de trabalho ingressa em um domínio, você deve emitir novamente os certificados ou configurar manualmente os sufixos DNS.  
  
## <a name="security"></a>Segurança  
 Como algumas das configurações relacionadas ao MSDTC e WS-AT são armazenadas no registro em HKLM\Software\Microsoft\MSDTC e em HKLM\Software\Microsoft\WSAT, respectivamente, certifique-se de que essas chaves do registro são protegidas para que somente os administradores podem gravar a eles. Na ferramenta do Editor do registro, clique com botão direito a chave que você deseja proteger e selecione **permissão** para definir o controle de acesso apropriado. É crucial para a segurança e integridade do sistema tão importante que as chaves são somente leitura para usuários com poucos privilégios.  
  
 Ao implantar o MSDTC, o administrador deve garantir que qualquer troca de dados do MSDTC é segura. Em uma implantação de grupo de trabalho, isolar a infra-estrutura transacional contra usuários mal-intencionados; em uma implantação de cluster, proteger o registro de cluster.  
  
## <a name="tracing"></a>Rastreamento  
 O serviço de protocolo WS-AT oferece suporte integrado, transações específicas de rastreamento que pode ser habilitado e gerenciado por meio do uso do [Snap-in MMC de configuração WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) ferramenta.  Rastreamentos podem incluir dados que indica a hora em que uma inscrição é feita para uma transação específica, o tempo que uma transação atinge seu estado terminal, o resultado a inscrição de cada transação tem recebido. Todos os rastreamentos podem ser exibidos usando o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ferramenta.  
  
 O serviço de protocolo WS-AT também dá suporte a rastreamento de ServiceModel integrado por meio da sessão de rastreamento ETW. Isso fornece rastreamentos mais detalhados, de comunicação específicos, além de rastreamentos de transação existentes.  Para habilitar esses rastreamentos adicionais, siga estas etapas  
  
1.  Abra o **iniciar/executar** menu, digite "regedit" na caixa de entrada e selecione **Okey**.  
  
2.  No **Editor do registro**, navegue até a seguinte pasta no painel esquerdo, Hkey_Local_Machine\SOFTWARE\Microsoft\WSAT\3.0\  
  
3.  Clique com botão direito do `ServiceModelDiagnosticTracing` de valor no painel direito e selecione **modificar**.  
  
4.  No **dados do valor** caixa de entrada, digite um dos seguintes valores válidos para especificar o nível de rastreamento que você deseja habilitar.  
  
-   0: desativado  
  
-   1: crítico  
  
-   3: erro. Esse é o valor padrão  
  
-   7: aviso  
  
-   15: informações  
  
-   31: detalhado  
  
## <a name="see-also"></a>Consulte também  
 [Utilitário de configuração de WS-AtomicTransaction (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)  
 [Snap-in do MMC de configuração de WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md)
