---
title: Configurando suporte de transações de WS-Atomic
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WS-AT protocol [WCF], configuring WS-Atomic Transaction
ms.assetid: cb9f1c9c-1439-4172-b9bc-b01c3e09ac48
caps.latest.revision: 31
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b2d94c96b8cc225344300540d9fc406a4742db2a
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="configuring-ws-atomic-transaction-support"></a>Configurando suporte de transações de WS-Atomic
Este tópico descreve como você pode configurar o suporte do WS-AtomicTransaction (WS-AT) usando o utilitário de configuração do WS-AT.  
  
## <a name="using-the-ws-at-configuration-utility"></a>Usando o utilitário de configuração WS-AT  
 O utilitário de configuração do WS-AT (wsatConfig.exe) é usado para definir as configurações do WS-AT. Para habilitar o serviço de protocolo WS-AT, você deve usar o utilitário de configuração para configurar a porta HTTPS para WS-AT, associar um certificado x. 509 para a porta HTTPS e configurar certificados de parceiro autorizado especificando nomes de entidade do certificado ou impressões digitais. O utilitário de configuração também permite que você selecione o modo de rastreamento e o conjunto padrão de saída e máximo entrada tempos limite de transação.  
  
 Você pode acessar a funcionalidade desta ferramenta usando um snap-in de página de propriedade de Microsoft Management Console (MMC) no console de gerenciamento de serviços de componente, ou em uma janela de linha de comando. Configurar o suporte do WS-AT no computador local por meio da janela de linha de comando. Defina configurações em computadores locais e remotos usando o snap-in do MMC.  
  
 A janela de linha de comando pode ser acessada no local de instalação do SDK do Windows "%WINDIR%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation".  
  
 Para obter mais informações sobre a ferramenta de linha de comando, consulte [o utilitário de configuração do WS-AtomicTransaction (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md).  
  
 Se você estiver executando [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ou [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], você pode acessar o snap-in do MMC, navegando para **controle administrativo/painel de ferramentas/serviços de componentes**, com o botão direito **meu computador**, e selecionando **propriedades**. Este é o mesmo local onde você pode configurar o Microsoft Distributed Transaction coordenador (MSDTC). Opções disponíveis para configuração são agrupadas sob o **WS-AT** guia. Se você estiver executando o Windows Vista ou [!INCLUDE[lserver](../../../../includes/lserver-md.md)], o snap-in do MMC pode ser encontrado clicando o **iniciar** botão e inserindo `dcomcnfg.exe` no **pesquisa** caixa. Quando o MMC é aberto, navegue até o **Meus Computer\Distributed transação Coordinator\Local DTC** nó, clique com botão direito e selecione **propriedades**. Opções disponíveis para configuração são agrupadas sob o **WS-AT** guia.  
  
 Para obter mais informações sobre o snap-in, consulte o [Snap-in MMC de configuração de WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md).  
  
 Para habilitar a interface do usuário da ferramenta, você deve primeiro registrar o arquivo WsatUI.dll, localizado no seguinte caminho  
  
 %ProgramFiles%\Microsoft SDKs\Windows\v6.0\Bin  
  
 Para registrar o produto, execute o seguinte comando em uma janela de Prompt de comando:  
  
 `regasm.exe /codebase WsatUI.dll`  
  
## <a name="enabling-ws-at"></a>Habilitando o WS-AT  
 Para habilitar o serviço de protocolo WS-AT em MSDTC usando a porta 443 e um certificado x. 509 com uma chave privada que foi instalada no repositório do computador local, use a ferramenta de wsatConfig.exe com o comando a seguir.  
  
 `WsatConfig.exe –network:enable –port:8443 –endpointCert:<machine|"Issuer\SubjectName"> -accountsCerts:<thumbprint|"Issuer\SubjectName"> -restart`  
  
 Substitua os respectivos parâmetros com valores relevantes para seu ambiente.  
  
 Para desabilitar o serviço de protocolo WS-AT em MSDTC, use a ferramenta de wsatConfig.exe com o comando a seguir.  
  
 `WsatConfig.exe –network:disable -restart`  
  
## <a name="configuring-trust-between-two-machines"></a>Configurar confiança entre dois computadores  
 O serviço de protocolo WS-AT requer que o administrador explicitamente Autorizar contas individuais para participar de transações distribuídas. Se você for um administrador para duas máquinas, você pode configurar os computadores para estabelecer uma relação de confiança mútua trocando o conjunto certo de certificados entre os computadores, instalá-los em armazenamentos de certificados apropriados e usando o ferramenta de wsatConfig.exe para adicionar o certificado de cada computador para a outra lista de certificados de participantes autorizados. Essa etapa é necessária para executar transações distribuídas entre dois computadores usando o WS-AT.  
  
 No exemplo a seguir descreve as etapas para estabelecer relação de confiança entre dois computadores, A e B.  
  
### <a name="creating-and-exporting-certificates"></a>Criar e exportar certificados  
 Este procedimento requer o snap-in MMC de certificados. O snap-in pode ser acessado, abrindo o menu Iniciar/Executar, digite "mmc" na caixa de entrada e pressionando Okey. Em seguida, no **Console1** janela, navegue até **arquivo/adicionar ou remover** Snap-in, clique em Adicionar e escolha **certificados** do **autônomos disponíveis Snap-ins** lista. Por fim, selecione **conta de computador** para gerenciar e clique em **Okey**. O **certificados** nó aparece no console do snap-in.  
  
 Você já deve ter os certificados necessários para estabelecer relação de confiança. Para saber como criar e instalar novos certificados antes das etapas a seguir, consulte [como: criar e instalar certificados de cliente temporários no WCF durante o desenvolvimento](http://go.microsoft.com/fwlink/?LinkId=158925).  
  
1.  Em um computador, usando a importação do snap-in MMC Certificados o certificado existente (certA) para o LocalMachine\MY (nó pessoal) e o armazenamento de LocalMachine\ROOT (nó de autoridade de certificação raiz confiável). Para importar um certificado para um nó específico, clique com botão direito no nó e escolha **todas as tarefas/importação**.  
  
2.  Na máquina B, usando o snap-in do MMC de certificados, crie ou obtenha certB um certificado com uma chave privada e importá-lo para o LocalMachine\MY (nó pessoal) e o armazenamento de LocalMachine\ROOT (nó de autoridade de certificação raiz confiável).  
  
3.  Exporte a chave pública do certA para um arquivo se isso não já foi feito.  
  
4.  Exporte a chave pública do certB para um arquivo se isso não já foi feito.  
  
### <a name="establishing-mutual-trust-between-machines"></a>Estabelecer relação de confiança mútua entre máquinas  
  
1.  Em um computador, importe a representação do arquivo de certB para os repositórios LocalMachine\MY e LocalMachine\ROOT. Isso declara que a máquina um certB de relações de confiança para se comunicar com ele.  
  
2.  Na máquina B, importe arquivo do certA para os repositórios LocalMachine\MY e LocalMachine\ROOT. Isso significa que a máquina B certA de relações de confiança para se comunicar com ele.  
  
 Depois de concluir essas etapas, a confiança é estabelecida entre os dois computadores e eles podem ser configurados para se comunicar entre si usando o WS-AT.  
  
### <a name="configuring-msdtc-to-use-certificates"></a>Configurar o MSDTC para usar certificados  
 Desde que o serviço de protocolo WS-AT atua como um cliente e um servidor, ele deve escutar conexões de entrada tanto iniciar conexões de saída. Portanto, você precisa configurar o MSDTC para que ele saiba qual certificado usar ao se comunicar com parceiros externos e os certificados para autorizar ao aceitar comunicação de entrada.  
  
 Você pode configurar isso usando o snap-in do MMC WS-AT. Para obter mais informações sobre essa ferramenta, consulte o [Snap-in MMC de configuração de WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) tópico. As etapas a seguir descrevem como estabelecer confiança entre dois computadores executando o MSDTC.  
  
1.  Defina configurações de máquina do. "Certificado do ponto de extremidade", selecione certA. Para "Autorizado certificados", selecione a certB.  
  
2.  Defina configurações da máquina B. "Certificado do ponto de extremidade", selecione certB. Para "Autorizado certificados", selecione a certA.  
  
> [!NOTE]
>  Quando um computador envia uma mensagem para a outra máquina, o remetente tenta verificar se o nome do assunto do certificado do destinatário e o nome da máquina do destinatário correspondem. Se eles não coincidirem, a verificação de certificado falhará e os dois computadores não podem se comunicar.  
>   
>  Para um computador que ingressou em um domínio, o nome é o nome de domínio totalmente qualificado. Por padrão, o nome de um computador em um grupo de trabalho é o nome da máquina NetBIOS. No entanto, o nome também pode incluir um sufixo do sistema de nome de domínio (DNS), se houver uma para a conexão que está sendo usado entre os dois computadores.  
>   
>  Se o nome da máquina for alterado, por exemplo, quando um computador de grupo de trabalho ingressa em um domínio, você deve emitir novamente os certificados ou configurar manualmente os sufixos DNS.  
  
## <a name="security"></a>Segurança  
 Como algumas das configurações relacionadas ao MSDTC e WS-AT são armazenadas no registro em HKLM\Software\Microsoft\MSDTC e em HKLM\Software\Microsoft\WSAT, respectivamente, certifique-se de que estas chaves do registro são protegidos para que somente os administradores podem escrever a eles. Na ferramenta do Editor do registro, clique com botão direito da chave que você deseja proteger e selecione **permissão** para definir o controle de acesso apropriadas. É fundamental para a segurança e a integridade do sistema que importante chaves são somente leitura para usuários com poucos privilégios.  
  
 Ao implantar o MSDTC, o administrador deve assegurar que qualquer intercâmbio de dados do MSDTC é seguro. Em uma implantação de grupo de trabalho, isolar a infraestrutura transacional contra usuários mal-intencionados; em uma implantação de cluster, proteja o registro de cluster.  
  
## <a name="tracing"></a>Rastreamento  
 O serviço de protocolo WS-AT oferece suporte integrado, transação rastreamento específico que pode ser habilitado e gerenciado por meio do uso do [Snap-in MMC de configuração de WS-AtomicTransaction](../../../../docs/framework/wcf/ws-atomictransaction-configuration-mmc-snap-in.md) ferramenta.  Rastreamentos podem incluir dados que indica o tempo que uma inscrição é feita para uma transação específica, a hora em que uma transação atinge seu estado terminal, o resultado de cada inscrição para transação recebeu. Todos os rastreamentos podem ser exibidos usando o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ferramenta.  
  
 O serviço de protocolo WS-AT também suporta o rastreio integrado ServiceModel através da sessão de rastreamento ETW. Isso fornece rastreamentos mais detalhados, específicas de comunicação, além de rastreamentos de transação existentes.  Para habilitar esses rastreamentos adicionais, siga estas etapas  
  
1.  Abra o **iniciar/executar** menu, digite "regedit" na caixa de entrada e selecione **Okey**.  
  
2.  No **Editor do registro**, navegue até a seguinte pasta no painel esquerdo, Hkey_Local_Machine\SOFTWARE\Microsoft\WSAT\3.0\  
  
3.  Clique com botão direito do `ServiceModelDiagnosticTracing` valor no painel direito e selecione **modificar**.  
  
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
