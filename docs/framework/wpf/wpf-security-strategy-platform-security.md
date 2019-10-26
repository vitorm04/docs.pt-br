---
title: Estratégia de segurança do WPF - segurança da plataforma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- platform security model [WPF]
- Common Language Runtime (CLR) security features
- operating system security model [WPF]
- Internet Explorer security features [WPF]
- Security-Critical method
- CLR security features [WPF]
- security model [WPF]
- security model [WPF], platform
- WPF [WPF], about security model
- Windows Presentation Foundation [WPF], about security model
- security model [WPF], operating system
ms.assetid: 2a39a054-3e2a-4659-bcb7-8bcea490ba31
ms.openlocfilehash: fdeb40f1e092f8c7e96e9d59e1b07673201fbe9d
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920384"
---
# <a name="wpf-security-strategy---platform-security"></a>Estratégia de segurança do WPF - segurança da plataforma
Embora o Windows Presentation Foundation (WPF) forneça uma variedade de serviços de segurança, ele também aproveita os recursos de segurança da plataforma subjacente, que inclui o sistema operacional, o CLR e o Internet Explorer. Essas camadas se combinam para fornecer [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] um modelo de segurança forte e de defesa intensa que tenta evitar qualquer ponto único de falha, conforme mostrado na figura a seguir:  
  
 ![Diagrama que mostra o modelo de segurança do WPF.](./media/wpf-security-strategy-platform-security/windows-presentation-foundation-security.png)  
  
 O restante deste tópico aborda os recursos em cada uma dessas camadas que pertencem a [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] especificamente.  

<a name="Operating_System_Security"></a>   
## <a name="operating-system-security"></a>Segurança do sistema operacional  
O núcleo do Windows fornece vários recursos de segurança que formam a base de segurança para todos os aplicativos do Windows, incluindo os criados com o WPF. Este tópico aborda a amplitude desses recursos de segurança que são importantes para o WPF, além de como o WPF se integra a eles para fornecer mais proteção aprofundada.  
  
<a name="Microsoft_Windows_XP_Service_Pack_2__SP2_"></a>   
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>SP2 (Microsoft Windows XP Service Pack 2)  
 Além de uma revisão geral e o fortalecimento do Windows, há três recursos principais do [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] que discutiremos neste tópico:  
  
- Compilação com /GS  
  
- [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)]  
  
#### <a name="gs-compilation"></a>Compilação com /GS  
 o [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] fornece proteção recompilando muitas bibliotecas principais do sistema, incluindo todas as dependências de [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], como o CLR, para ajudar a mitigar estouros de buffer. Isso é feito pelo uso do parâmetro /GS com o compilador de linha de comando C/C++. Embora seja necessário evitar estouros de buffer explicitamente, a compilação com /GS fornece um exemplo de uma proteção extensa contra possíveis vulnerabilidades que são criadas de maneira inadvertida ou mal-intencionada por eles.  
  
 Historicamente, os estouros de buffer tem sido a causa de diversas explorações de segurança de alto impacto. Um estouro de buffer ocorre quando um invasor aproveita uma vulnerabilidade de código que permite a injeção de um código mal-intencionado escrito além dos limites de um buffer. Em seguida, isso permite que um invasor sequestre o processo no qual o código está em execução, substituindo o endereço de retorno de uma função para fazer com que o código do invasor seja executado. O resultado é um código mal-intencionado que executa um código arbitrário com os mesmos privilégios do processo sequestrado.  
  
 Em um alto nível, o sinalizador do compilador-GS protege contra algumas saturações de buffer em potencial injetando um cookie de segurança especial para proteger o endereço de retorno de uma função que tem buffers de cadeia de caracteres locais. Após o retorno de uma função, o cookie de segurança é comparado com seu valor anterior. Se o valor tiver sido alterado, poderá ter ocorrido um estouro de buffer e o processo será interrompido com uma condição de erro. A interrupção do processo impede a execução do código potencialmente mal-intencionado. Consulte [-GS (verificação de segurança do buffer)](/cpp/build/reference/gs-buffer-security-check) para obter mais detalhes.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] é compilado com o sinalizador/GS para adicionar ainda outra camada de defesa para [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplicativos.  
  
#### <a name="microsoft-windows-update-enhancements"></a>Melhorias do Microsoft Windows Update  
 [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)] também foi aprimorada no [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] para simplificar o processo de download e instalação de atualizações. Essas alterações melhoram significativamente a segurança para os clientes [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], ajudando a garantir que seus sistemas estejam atualizados, particularmente em relação às atualizações de segurança.  
  
<a name="Windows_Vista"></a>   
### <a name="windows-vista"></a>Windows Vista  
Os usuários do WPF no Windows Vista se beneficiarão dos aprimoramentos de segurança adicionais do sistema operacional, incluindo "acesso de usuário com privilégios mínimos", verificações de integridade de código e isolamento de privilégio.  
  
#### <a name="user-account-control-uac"></a>UAC (Controle de Conta de Usuário)  
 Hoje, os usuários do Windows tendem a executar com privilégios de administrador, pois muitos aplicativos exigem a instalação ou execução, ou ambos. Ter a capacidade de escrever configurações de aplicativo padrão no Registro é um exemplo.  
  
 De fato, a execução com privilégios de administrador significa que os aplicativos são executados em processos que receberam privilégios de administrador. O impacto de segurança disto é que qualquer código mal-intencionado que sequestre um processo executado com privilégios de administrador herdará automaticamente esses privilégios, incluindo o acesso a recursos críticos do sistema.  
  
 Uma maneira de se proteger contra essa ameaça de segurança é executar aplicativos com o mínimo de privilégios necessários. Isso é conhecido como o princípio de privilégios mínimos e é um recurso básico do sistema operacional Windows. Esse recurso é chamado de UAC (controle de conta de usuário) e é usado pelo Windows UAC de duas maneiras principais:  
  
- Para executar a maioria dos aplicativos com privilégios UAC por padrão, mesmo se o usuário for um administrador; somente os aplicativos que precisam de privilégios de administrador serão executados com privilégios de administrador. Para serem executados com privilégios administrativos, os aplicativos devem ser explicitamente marcados em seus manifestos do aplicativo ou como uma entrada na política de segurança.  
  
- Para fornecer soluções de compatibilidade como virtualização. Por exemplo, vários aplicativos tentam gravar em localizações restritas como C:\Program Files. Para os aplicativos executados no UAC, existe uma localização alternativa por usuário que não exige privilégios de administrador para ser usada para gravação. Para os aplicativos executados no UAC, o UAC virtualiza C:\Program Files para que os aplicativos que acreditam que estão fazendo gravações nele, na verdade, estão gravando na localização alternativa por usuário. Esse tipo de trabalho de compatibilidade permite que o sistema operacional execute vários aplicativos que anteriormente não podiam ser executados no UAC.  
  
#### <a name="code-integrity-checks"></a>Verificações de integridade de código  
 O Windows Vista incorpora verificações de integridade de código mais profundas para ajudar a impedir que códigos mal-intencionados sejam injetados em arquivos do sistema ou no kernel em tempo de carga/execução. Isso vai além da proteção de arquivo do sistema.  
  
<a name="Limited_Rights_Process_for_Browser_Hosted_Applications"></a>   
### <a name="limited-rights-process-for-browser-hosted-applications"></a>Processos com direitos limitados para aplicativos hospedados pelo navegador  
 Os aplicativos [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] hospedados no navegador são executados na área restrita da zona da Internet. a integração do [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] com o Microsoft Internet Explorer estende essa proteção com suporte adicional.  
  
 Como os [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] geralmente são protegidos pelo conjunto de permissões da zona da Internet, a remoção desses privilégios não prejudica [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] de uma perspectiva de compatibilidade. Em vez disso, é criada uma camada adicional de proteção extensa; se um aplicativo em área restrita puder explorar outras camadas e sequestrar o processo, ainda assim, o processo apenas terá privilégios limitados.  
  
 Consulte [usando uma conta de usuário com privilégios mínimos](https://docs.microsoft.com/previous-versions/tn-archive/cc700846%28v=technet.10%29).  
  
<a name="Common_Language_Runtime_Security"></a>   
## <a name="common-language-runtime-security"></a>Segurança do Common Language Runtime  
 O Common Language Runtime (CLR) oferece vários benefícios-chave de segurança que incluem validação e verificação, CAS (segurança de acesso ao código) e a metodologia crítica de segurança.  
  
<a name="Validation_and_Verification"></a>   
### <a name="validation-and-verification"></a>Validação e verificação  
 Para fornecer isolamento de assembly e integridade, o CLR usa um processo de validação. A validação do CLR garante que os assemblies sejam isolados validando seu formato de arquivo PE (executável portátil) para endereços que apontam para fora do assembly. A validação de CLR também valida a integridade dos metadados que são inseridos em um assembly.  
  
 Para garantir a segurança de tipo, ajude a evitar problemas comuns de segurança (por exemplo, saturações de buffer) e habilitar a área restrita por meio do isolamento de subprocesso, a segurança do CLR usa o conceito de verificação.  
  
 Os aplicativos gerenciados são compilados em MSIL (Microsoft Intermediate Language). Quando os métodos em um aplicativo gerenciado são executados, a MSIL é compilada em código nativo por meio da compilação JIT (Just-In-Time). A compilação JIT inclui um processo de verificação que aplica várias regras de segurança e robustez que garantem que o código não:  
  
- Viola contratos de tipos  
  
- Introduz estouros de buffer  
  
- Acessa a memória de forma ampla.  
  
 O código gerenciado que não está em conformidade com as regras de verificação não tem permissão de ser executado, a menos que seja considerado um código confiável.  
  
 A vantagem do código verificável é um motivo importante pelo qual [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] se baseia na .NET Framework. Na medida em que um código verificável é usado, a possibilidade de exploração de possíveis vulnerabilidades é consideravelmente reduzida.  
  
<a name="Code_Access_Security"></a>   
### <a name="code-access-security"></a>Segurança de acesso do código  
 Um computador cliente expõe uma grande variedade de recursos aos quais um aplicativo gerenciado pode ter acesso, incluindo o sistema de arquivos, o Registro, serviços de impressão, a interface do usuário, reflexão e variáveis de ambiente. Antes que um aplicativo gerenciado possa acessar qualquer um dos recursos em um computador cliente, ele deve ter .NET Framework permissão para fazer isso. Uma permissão no CAS é uma subclasse da <xref:System.Security.CodeAccessPermission>; O CAS implementa uma subclasse para cada recurso que os aplicativos gerenciados podem acessar.  
  
 O conjunto de permissões que um aplicativo gerenciado recebe pelo CAS quando ele começa a ser executado é conhecido como um conjunto de permissões e é determinado pelas evidências fornecidas pelo aplicativo. Para os aplicativos [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], a evidência fornecida é o local, ou zona, do qual os aplicativos são iniciados. O CAS identifica as seguintes zonas:  
  
- **Meu Computador**. Aplicativos iniciados no computador cliente (Totalmente Confiável).  
  
- **Intranet local**. Aplicativos iniciados na intranet. (Um Pouco Confiáveis).  
  
- **Internet**. Aplicativos iniciados na Internet. (Os Menos Confiáveis).  
  
- **Sites confiáveis**. Aplicativos identificados por um usuário como sendo confiáveis. (Os Menos Confiáveis).  
  
- **Sites não confiáveis**. Aplicativos identificados por um usuário como sendo não confiáveis. (Não Confiáveis).  
  
 Para cada uma dessas zonas, o CAS fornece um conjunto de permissões predefinido que inclui as permissões que correspondem ao nível de confiança associado a cada um. Elas incluem:  
  
- **FullTrust**. Para aplicativos iniciados na zona de **meu computador** . Todas as permissões possíveis são concedidas.  
  
- **LocalIntranet**. Para aplicativos iniciados na zona **da intranet local** . Um subconjunto de permissões é concedido para fornecer acesso moderado aos recursos do computador cliente, incluindo armazenamento isolado, acesso irrestrito à interface do usuário, caixas de diálogo de arquivo irrestritas, reflexão limitada e acesso limitado a variáveis de ambiente. Permissões para recursos críticos, como o Registro, não são fornecidas.  
  
- **Internet**. Para aplicativos iniciados na zona **Internet** ou **sites confiáveis** . Um subconjunto de permissões é concedido para permitir acesso limitado aos recursos do computador cliente, incluindo armazenamento isolado, somente abertura de arquivo e interface do usuário limitada. Essencialmente, esse conjunto de permissões isola os aplicativos do computador cliente.  
  
 Os aplicativos identificados como sendo da zona **sites não confiáveis** não recebem permissões por CAS. Consequentemente, não existe um conjunto de permissões predefinidas para eles.  
  
 A figura a seguir ilustra a relação entre zonas, conjuntos de permissões, permissões e recursos:  
  
 ![Diagrama que mostra os conjuntos de permissões CAS.](./media/wpf-security-strategy-platform-security/code-access-security-permissions-relationship.png)  
  
 As restrições da área restrita de segurança de zona da Internet aplicam-se igualmente a qualquer código que um XBAP importa de uma biblioteca do sistema, incluindo [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Isso garante que cada bit do código seja bloqueado, até mesmo [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Infelizmente, para ser capaz de executar o, um XBAP precisa executar a funcionalidade que exige mais permissões do que aquelas habilitadas pela área restrita de segurança da zona da Internet.  
  
 Considere um aplicativo XBAP que inclui a seguinte página:  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Para executar esse XBAP, o código de [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] subjacente deve executar mais funcionalidade do que o que está disponível para o XBAP de chamada, incluindo:  
  
- Criando um identificador de janela (HWND) para renderização  
  
- Expedição de mensagens  
  
- Carregamento da fonte Tahoma  
  
 De um ponto de vista de segurança, permitir o acesso direto a qualquer uma dessas operações pelo aplicativo em área restrita seria catastrófico.  
  
 Felizmente, [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] atende a essa situação, permitindo que essas operações sejam executadas com privilégios elevados em nome do aplicativo em área restrita. Embora todas as operações de [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] sejam verificadas em relação às permissões de segurança de zona da Internet limitadas do domínio do aplicativo do XBAP, [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] (como com outras bibliotecas do sistema) recebe um conjunto de permissões que inclui todas as permissões possíveis.
  
 Isso requer que [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] receba privilégios elevados ao impedir que esses privilégios sejam regidos pelo conjunto de permissões de zona da Internet do domínio do aplicativo host.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] faz isso usando o método **Assert** de uma permissão. O código a seguir mostra como isso acontece.  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Essencialmente, a **Assert** impede que as permissões ilimitadas exigidas pelo [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] sejam restritas pelas permissões de zona da Internet do XBAP.  
  
 Do ponto de vista da plataforma, [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] é responsável por usar o **Assert** corretamente; um uso incorreto de **Assert** pode permitir que o código mal-intencionado eleve privilégios. Consequentemente, é importante chamar **Assert** apenas quando necessário e garantir que as restrições de área restrita permaneçam intactas. Por exemplo, um código em área restrita não tem permissão para abrir arquivos aleatórios, mas tem permissão para usar fontes. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] permite que os aplicativos em área restrita usem a funcionalidade de fonte chamando **Assert**e para [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] ler arquivos conhecidos por conter essas fontes em nome do aplicativo em área restrita.  
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>Implantação do ClickOnce  
 O ClickOnce é uma tecnologia de implantação abrangente que está incluída com o .NET Framework e se integra ao Visual Studio (consulte [segurança e implantação do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) para obter informações detalhadas). Os aplicativos [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] autônomos podem ser implantados usando o ClickOnce, enquanto aplicativos hospedados em navegador devem ser implantados com o ClickOnce.  
  
 Os aplicativos implantados usando o ClickOnce recebem uma camada de segurança adicional sobre a CAS (segurança de acesso ao código); essencialmente, os aplicativos implantados pelo ClickOnce solicitam as permissões necessárias. Eles recebem somente as permissões se eles não excedem o conjunto de permissões para a zona da qual o aplicativo é implantado. Ao reduzir o conjunto de permissões apenas para aqueles que são necessários, mesmo que eles sejam menores do que os fornecidos pelo conjunto de permissões da zona de inicialização, o número de recursos aos quais o aplicativo tem acesso é reduzido para um mínimo. Consequentemente, se o aplicativo for sequestrado, o potencial de danos ao computador cliente será reduzido.  
  
<a name="Security_Critical_Methodology"></a>   
### <a name="security-critical-methodology"></a>Metodologia Crítica para Segurança  
 O código de [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] que usa permissões para habilitar a área restrita da zona da Internet para aplicativos XBAP deve ser mantido no nível mais alto possível de auditoria e controle de segurança. Para facilitar esse requisito, .NET Framework fornece novo suporte para o gerenciamento de código que eleva o privilégio. Especificamente, o CLR permite que você identifique o código que eleva o privilégio e marque-o com o <xref:System.Security.SecurityCriticalAttribute>; qualquer código não marcado com <xref:System.Security.SecurityCriticalAttribute> se torna *transparente* usando essa metodologia. Por outro lado, o código gerenciado que não está marcado com <xref:System.Security.SecurityCriticalAttribute> é impedido de elevar o privilégio.  
  
 A metodologia de segurança crítica permite que a organização de [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] código que eleva o privilégio em *kernel de segurança crítica*, com o restante sendo transparente. Isolar o código de segurança crítica permite que a equipe de engenharia de [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] focalize uma análise de segurança adicional e um controle do código-fonte no kernel crítico de segurança acima e além das práticas de segurança padrão (consulte [estratégia de segurança do WPF – segurança Engenharia](wpf-security-strategy-security-engineering.md)).  
  
 Observe que .NET Framework permite que o código confiável estenda a área restrita da zona da Internet do XBAP, permitindo que os desenvolvedores gravem assemblies gerenciados marcados com o <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) e implantados no GAC (cache de assembly global) do usuário. Marcar um assembly com um APTCA é uma operação de segurança altamente confidencial, pois permite que qualquer código chame esse assembly, incluindo um código mal-intencionado da Internet. Deve-se ter extremo cuidado e usar as melhores práticas ao fazer isso e os usuários devem optar por confiar nesse software para que ele seja instalado.  
  
<a name="Microsoft_Internet_Explorer_Security"></a>   
## <a name="microsoft-internet-explorer-security"></a>Segurança do Microsoft Internet Explorer  
 Além de reduzir os problemas de segurança e simplificar a configuração de segurança, o Microsoft Internet Explorer 6 (SP2) contém vários recursos que aprimoram a segurança para os usuários de [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]. O foco desses recursos tenta permitir aos usuários um maior controle sobre sua experiência de navegação.  
  
 Antes do IE6 SP2, os usuários podem estar sujeitos a qualquer um dos seguintes:  
  
- Janelas pop-up aleatórias.  
  
- Redirecionamento de script confuso.  
  
- Várias caixas de diálogo de segurança em alguns sites.  
  
 Em alguns casos, sites não confiáveis tentam enganar os usuários por meio da falsificação da instalação [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] ou mostrando repetidamente uma caixa de diálogo de instalação do Microsoft ActiveX, embora o usuário possa tê-lo cancelado. Usando essas técnicas, é possível que um número significativo de usuários tenha sido levado a tomar decisões erradas que resultaram na instalação de aplicativos spyware.  
  
 O IE6 SP2 inclui vários recursos para atenuar esses tipos de problemas, que giram em volta do conceito de iniciação do usuário. O IE6 SP2 detecta quando um usuário clicou em um elemento link ou Page antes de uma ação, que é conhecida como *inicialização do usuário*, e o trata de forma diferente de quando uma ação semelhante é disparada pelo script em uma página. Por exemplo, o IE6 SP2 incorpora um **bloqueador de pop-ups** que detecta quando um usuário clica em um botão antes da página que cria um pop-up. Isso permite que o IE6 SP2 permita os pop-ups mais inofensivos enquanto impede pop-ups que os usuários não pedem nem desejam. Os pop-ups bloqueados são interceptados na nova **barra de informações**, que permite ao usuário substituir manualmente o bloco e exibir o pop-up.  
  
 A mesma lógica de inicialização do usuário também é aplicada para **abrir** /**salvar** prompts de segurança. As caixas de diálogo de instalação do ActiveX são sempre interceptadas na barra de informações, a menos que elas representem uma atualização de um controle instalado anteriormente. Essas medidas são combinadas para fornecer aos usuários uma experiência do usuário mais segura e mais controlada, já que eles estão protegidos contra sites que os induzem a instalar software indesejado ou mal-intencionado.  
  
 Esses recursos também protegem os clientes que usam o IE6 SP2 para navegar para sites que permitem que eles baixem e instalem aplicativos [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Em particular, isso ocorre porque o IE6 SP2 oferece uma experiência de usuário melhor que reduz a chance de os usuários instalarem aplicativos mal-intencionados ou espertodos independentemente de qual tecnologia foi usada para compilá-lo, incluindo [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. o [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] adiciona essas proteções usando o ClickOnce para facilitar o download de seus aplicativos pela Internet. Como [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] executado em uma área restrita de segurança de zona da Internet, eles podem ser iniciados diretamente. Por outro lado, os aplicativos [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] autônomos exigem confiança total para serem executados. Para esses aplicativos, o ClickOnce exibirá uma caixa de diálogo de segurança durante o processo de inicialização para notificar o uso dos requisitos de segurança adicionais do aplicativo. No entanto, isso deve ser iniciado pelo usuário, também será regido pela lógica iniciada pelo usuário e pode ser cancelado.  
  
 O Internet Explorer 7 incorpora e estende os recursos de segurança do IE6 SP2 como parte de um compromisso contínuo com a segurança.  
  
## <a name="see-also"></a>Consulte também

- [Segurança de acesso do código](../misc/code-access-security.md)
- [Security](security-wpf.md)
- [Segurança parcialmente confiável do WPF](wpf-partial-trust-security.md)
- [Estratégia de segurança do WPF – Engenharia de segurança](wpf-security-strategy-security-engineering.md)
