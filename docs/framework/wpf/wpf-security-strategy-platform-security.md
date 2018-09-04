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
ms.openlocfilehash: 905092cfdcbcbeb95fdfa689c09a847491595d9d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43560386"
---
# <a name="wpf-security-strategy---platform-security"></a>Estratégia de segurança do WPF - segurança da plataforma
Embora o Windows Presentation Foundation (WPF) fornece uma variedade de serviços de segurança, ele também utiliza os recursos de segurança da plataforma subjacente, que inclui o sistema operacional, o [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)], e [!INCLUDE[TLA2#tla_ie](../../../includes/tla2sharptla-ie-md.md)]. Essas camadas são combinadas para fornecer [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] um modelo de segurança forte e defesa em profundidade que tenta evitar pontos únicos de falha, conforme mostrado na figura a seguir:  
  
 ![Ilustração de segurança do WPF](../../../docs/framework/wpf/media/windowplatformsecurity.PNG "windowplatformsecurity")  
  
 O restante deste tópico aborda os recursos em cada uma dessas camadas que pertencem ao [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] especificamente.  
  

  
<a name="Operating_System_Security"></a>   
## <a name="operating-system-security"></a>Segurança do sistema operacional  
 O nível mínimo de sistema operacional que é exigido pelo [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] é [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)]. O núcleo da [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] fornece vários recursos de segurança que formam a base de segurança para todos os aplicativos do Windows, incluindo aqueles criados com [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] incorpora os recursos de segurança do [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] e estende-os ainda mais. Este tópico aborda a amplitude desses recursos de segurança que são importantes para [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], bem como [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] integra-se com eles para fornecer ainda mais defesa em profundidade.  
  
<a name="Microsoft_Windows_XP_Service_Pack_2__SP2_"></a>   
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>SP2 (Microsoft Windows XP Service Pack 2)  
 Além de uma revisão geral e fortalecendo do Windows, há três recursos principais do [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] que discutiremos neste tópico:  
  
-   Compilação com /GS  
  
-   [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)].  
  
#### <a name="gs-compilation"></a>Compilação com /GS  
 [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] fornece proteção por meio da recompilação muitas bibliotecas principais do sistema, incluindo todos os [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] dependências, como o [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)], para ajudar a atenuar estouros de buffer. Isso é feito pelo uso do parâmetro /GS com o compilador de linha de comando C/C++. Embora seja necessário evitar estouros de buffer explicitamente, a compilação com /GS fornece um exemplo de uma proteção extensa contra possíveis vulnerabilidades que são criadas de maneira inadvertida ou mal-intencionada por eles.  
  
 Historicamente, os estouros de buffer tem sido a causa de diversas explorações de segurança de alto impacto. Um estouro de buffer ocorre quando um invasor aproveita uma vulnerabilidade de código que permite a injeção de um código mal-intencionado escrito além dos limites de um buffer. Em seguida, isso permite que um invasor sequestre o processo no qual o código está em execução, substituindo o endereço de retorno de uma função para fazer com que o código do invasor seja executado. O resultado é um código mal-intencionado que executa um código arbitrário com os mesmos privilégios do processo sequestrado.  
  
 Em um alto nível, o sinalizador do compilador /GS protege contra alguns possíveis estouros de buffer injetando um cookie de segurança especial para proteger o endereço de retorno de uma função que tem buffers de cadeia de caracteres local. Após o retorno de uma função, o cookie de segurança é comparado com seu valor anterior. Se o valor tiver sido alterado, poderá ter ocorrido um estouro de buffer e o processo será interrompido com uma condição de erro. A interrupção do processo impede a execução do código potencialmente mal-intencionado. Ver [/GS (Buffer Security Check)](https://msdn.microsoft.com/library/8dbf701c.aspx) para obter mais detalhes.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] é compilado com o sinalizador /GS para adicionar outra camada de defesa para [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplicativos.  
  
#### <a name="microsoft-windows-update-enhancements"></a>Melhorias do Microsoft Windows Update  
 [!INCLUDE[TLA#tla_win_update](../../../includes/tlasharptla-win-update-md.md)] também foi aprimorado no [!INCLUDE[TLA2#tla_winxpsp2](../../../includes/tla2sharptla-winxpsp2-md.md)] para simplificar o processo de download e instalação de atualizações. Essas alterações melhoram significativamente a segurança para [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] clientes, ajudando a garantir que seus sistemas estão atualizados, especialmente com relação a atualizações de segurança.  
  
<a name="Windows_Vista"></a>   
### <a name="windows-vista"></a>Windows Vista  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] os usuários em [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] irá se beneficiar de aprimoramentos de segurança adicionais do sistema operacional, incluindo "Privilégios mínimos acesso de usuário", verificações de integridade de código e isolamento de privilégio.  
  
#### <a name="user-account-control-uac"></a>UAC (Controle de Conta de Usuário)  
 Atualmente, os usuários do Windows tendem a executar com privilégios de administrador, pois muitos aplicativos exigem-las para instalação ou execução ou ambos. Ter a capacidade de escrever configurações de aplicativo padrão no Registro é um exemplo.  
  
 De fato, a execução com privilégios de administrador significa que os aplicativos são executados em processos que receberam privilégios de administrador. O impacto de segurança disto é que qualquer código mal-intencionado que sequestre um processo executado com privilégios de administrador herdará automaticamente esses privilégios, incluindo o acesso a recursos críticos do sistema.  
  
 Uma maneira de se proteger contra essa ameaça de segurança é executar aplicativos com o mínimo de privilégios necessários. Isso é conhecido como o princípio de privilégio mínimo e é um recurso fundamental do [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] sistema operacional. Esse recurso é chamado de controle de conta de usuário (UAC) e é usado pelo [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] UAC de duas maneiras principais:  
  
-   Para executar a maioria dos aplicativos com privilégios UAC por padrão, mesmo se o usuário for um administrador; somente os aplicativos que precisam de privilégios de administrador serão executados com privilégios de administrador. Para serem executados com privilégios administrativos, os aplicativos devem ser explicitamente marcados em seus manifestos do aplicativo ou como uma entrada na política de segurança.  
  
-   Para fornecer soluções de compatibilidade como virtualização. Por exemplo, vários aplicativos tentam gravar em localizações restritas como C:\Program Files. Para os aplicativos executados no UAC, existe uma localização alternativa por usuário que não exige privilégios de administrador para ser usada para gravação. Para os aplicativos executados no UAC, o UAC virtualiza C:\Program Files para que os aplicativos que acreditam que estão fazendo gravações nele, na verdade, estão gravando na localização alternativa por usuário. Esse tipo de trabalho de compatibilidade permite que o sistema operacional execute vários aplicativos que anteriormente não podiam ser executados no UAC.  
  
#### <a name="code-integrity-checks"></a>Verificações de integridade de código  
 O [!INCLUDE[TLA#tla_longhorn](../../../includes/tlasharptla-longhorn-md.md)] incorpora verificações de integridade de código mais profundas para ajudar a impedir que um código mal-intencionado seja injetado em arquivos do sistema ou no kernel em tempo de carregamento/execução. Isso vai além da proteção de arquivo do sistema.  
  
<a name="Limited_Rights_Process_for_Browser_Hosted_Applications"></a>   
### <a name="limited-rights-process-for-browser-hosted-applications"></a>Processos com direitos limitados para aplicativos hospedados pelo navegador  
 Hospedados pelo navegador [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplicativos executados dentro de área restrita da zona da Internet. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] integração com o [!INCLUDE[TLA#tla_ie](../../../includes/tlasharptla-ie-md.md)] estende essa proteção com suporte adicional.  
  
#### <a name="internet-explorer-6-service-pack-2-and-internet-explorer-7-for-xp"></a>Internet Explorer 6 Service Pack 2 e Internet Explorer 7 para XP  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aproveita a segurança do sistema operacional, limitando os privilégios do processo do [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] para aumentar a proteção. Antes de um hospedados pelo navegador [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplicativo é iniciado, o sistema operacional cria um processo de host que remove os privilégios desnecessários do token do processo. Alguns exemplos de privilégios que são removidos incluem a capacidade de desligar o computador do usuário, carregar drivers e obter acesso de leitura a todos os arquivos no computador.  
  
#### <a name="internet-explorer-7-for-vista"></a>Internet Explorer 7 para Vista  
 Na [!INCLUDE[TLA#tla_ie7](../../../includes/tlasharptla-ie7-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplicativos executados no modo protegido. Especificamente, [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)] executados com integridade de nível médio.  
  
#### <a name="defense-in-depth-layer"></a>Camada de proteção extensa  
 Uma vez que [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] são geralmente em área restrita pelo conjunto de permissões da zona, remoção desses privilégios não prejudica Internet [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] de uma perspectiva de compatibilidade. Em vez disso, é criada uma camada adicional de proteção extensa; se um aplicativo em área restrita puder explorar outras camadas e sequestrar o processo, ainda assim, o processo apenas terá privilégios limitados.  
  
 Ver [usando uma conta de usuário com privilégios mínimos](https://technet.microsoft.com/library/cc700846.aspx).  
  
<a name="Common_Language_Runtime_Security"></a>   
## <a name="common-language-runtime-security"></a>Segurança do Common Language Runtime  
 O [!INCLUDE[TLA#tla_clr](../../../includes/tlasharptla-clr-md.md)] oferece vários benefícios importantes de segurança que incluem validação e verificação, [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)]e a metodologia crítica para segurança.  
  
<a name="Validation_and_Verification"></a>   
### <a name="validation-and-verification"></a>Validação e verificação  
 Para fornecer isolamento de assembly e integridade, o [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] usa um processo de validação. A validação do [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] garante que os assemblies são isolados com a validação de seu formato de arquivo PE (Portable Executable) para endereços que apontam para fora do assembly. A validação do [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] também valida a integridade dos metadados inseridos em um assembly.  
  
 Para garantir a segurança de tipos, ajudar a evitar problemas comuns de segurança (por exemplo, estouros de buffer) e habilitar a área restrita por meio do isolamento de subprocessos, [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] security usa o conceito de verificação.  
  
 Os aplicativos gerenciados são compilados em MSIL (Microsoft Intermediate Language). Quando os métodos em um aplicativo gerenciado são executados, a MSIL é compilada em código nativo por meio da compilação JIT (Just-In-Time). A compilação JIT inclui um processo de verificação que aplica várias regras de segurança e robustez que garantem que o código não:  
  
-   Viola contratos de tipos  
  
-   Introduz estouros de buffer  
  
-   Acessa a memória de forma ampla.  
  
 O código gerenciado que não está em conformidade com as regras de verificação não tem permissão de ser executado, a menos que seja considerado um código confiável.  
  
 A vantagem de ter código verificável é dos principais motivos pelos quais [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] se baseia no .NET Framework. Na medida em que um código verificável é usado, a possibilidade de exploração de possíveis vulnerabilidades é consideravelmente reduzida.  
  
<a name="Code_Access_Security"></a>   
### <a name="code-access-security"></a>Segurança de acesso do código  
 Um computador cliente expõe uma grande variedade de recursos aos quais um aplicativo gerenciado pode ter acesso, incluindo o sistema de arquivos, o Registro, serviços de impressão, a interface do usuário, reflexão e variáveis de ambiente. Para que um aplicativo gerenciado possa acessar qualquer um dos recursos em um computador cliente, ele deve ter permissão do .NET Framework para fazer isso. Uma permissão na [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] é uma subclasse do <xref:System.Security.CodeAccessPermission>; [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] implementa uma subclasse para cada recurso que os aplicativos gerenciados pode acessar.  
  
 O conjunto de permissões que um aplicativo gerenciado é concedido por [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] quando ele inicia a execução é conhecido como um conjunto de permissões e é determinado pela evidência fornecida pelo aplicativo. Para [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplicativos, a evidência fornecida é o local, ou zona, da qual os aplicativos são iniciados. O [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] identifica as seguintes zonas:  
  
-   **Meu Computador**. Aplicativos iniciados no computador cliente (Totalmente Confiável).  
  
-   **Intranet local**. Aplicativos iniciados na intranet. (Um Pouco Confiáveis).  
  
-   **Internet**. Aplicativos iniciados na Internet. (Os Menos Confiáveis).  
  
-   **Sites confiáveis**. Aplicativos identificados por um usuário como sendo confiáveis. (Os Menos Confiáveis).  
  
-   **Sites não confiáveis**. Aplicativos identificados por um usuário como sendo não confiáveis. (Não Confiáveis).  
  
 Para cada uma dessas zonas, [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] fornece um conjunto de permissões predefinidas que inclui as permissões que corresponde ao nível de confiança associado a cada. Elas incluem:  
  
-   **FullTrust**. Para aplicativos iniciados a partir de **meu computador** zona. Todas as permissões possíveis são concedidas.  
  
-   **LocalIntranet**. Para aplicativos iniciados a partir de **Intranet Local** zona. Um subconjunto de permissões é concedido para fornecer acesso moderado aos recursos do computador cliente, incluindo armazenamento isolado, acesso irrestrito à interface do usuário, caixas de diálogo de arquivo irrestritas, reflexão limitada e acesso limitado a variáveis de ambiente. Permissões para recursos críticos, como o Registro, não são fornecidas.  
  
-   **Internet**. Para aplicativos iniciados a partir de **Internet** ou **Sites confiáveis** zona. Um subconjunto de permissões é concedido para permitir acesso limitado aos recursos do computador cliente, incluindo armazenamento isolado, somente abertura de arquivo e interface do usuário limitada. Basicamente, esses conjuntos de permissões isolam os aplicativos do computador cliente.  
  
 Aplicativos identificados como sendo do **Sites não confiáveis** zona não recebem permissões por [!INCLUDE[TLA2#tla_cas](../../../includes/tla2sharptla-cas-md.md)] em todos os. Consequentemente, não existe um conjunto de permissões predefinidas para eles.  
  
 A figura a seguir ilustra o relacionamento entre zonas, conjuntos de permissões, permissões e recursos.  
  
 ![Conjuntos de permissões do CAS](../../../docs/framework/wpf/media/caspermissionsets.png "CASPermissionSets")  
  
 As restrições da Internet em área restrita da zona se aplicam igualmente a qualquer código que um [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] importa de uma biblioteca do sistema, incluindo [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Isso garante que cada pedaço do código está bloqueada, até mesmo [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. Infelizmente, para poder ser executado, um [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] precisa executar funcionalidades que requer mais permissões do que aquelas habilitadas pela área restrita segurança da zona da Internet.  
  
 Considere um [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] aplicativo que inclua a seguinte página:  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Para executar esta [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)], subjacente [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] código deve executar mais funcionalidades que está disponível para a chamada [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)], incluindo:  
  
-   Criação de um identificador de janela (hWnd) para renderização  
  
-   Expedição de mensagens  
  
-   Carregamento da fonte Tahoma  
  
 De um ponto de vista de segurança, permitir o acesso direto a qualquer uma dessas operações pelo aplicativo em área restrita seria catastrófico.  
  
 Felizmente, [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] lida com essa situação, permitindo que essas operações sejam executadas com privilégios elevados em nome do aplicativo em área restrita. Enquanto tudo [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] operações são comparadas com as permissões de segurança de zona da Internet limitadas do domínio de aplicativo do [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)], [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] (assim como acontece com outras bibliotecas do sistema) é concedido um conjunto de permissões que inclui todos os possíveis permissões  
  
 Isso requer que [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] receba privilégios elevados, enquanto impede que esses privilégios sejam regidos pelo conjunto de permissões da zona da Internet do domínio do aplicativo host.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] faz isso usando o **Assert** método de uma permissão. O código a seguir mostra como isso acontece.  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 O **Assert** essencialmente impede que as permissões ilimitadas exigidas pelo [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] permissões da zona sejam restritas por Internet o [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)].  
  
 De uma perspectiva de plataforma [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] é responsável por usar **Assert** corretamente; um uso incorreto de **Assert** pode permitir que código mal-intencionado eleve privilégios. Consequentemente, é importante, em seguida, chamar apenas **Assert** quando necessário, e para garantir que essa área restrita restrições permanecem intactas. Por exemplo, um código em área restrita não tem permissão para abrir arquivos aleatórios, mas tem permissão para usar fontes. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] permite que os aplicativos de área restrita e usar a funcionalidade de fonte chamando **Assert**e para [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] leia arquivos conhecidos que contêm essas fontes em nome do aplicativo em área restrita.  
  
<a name="ClickOnce_Deployment"></a>   
### <a name="clickonce-deployment"></a>Implantação do ClickOnce  
 [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] é uma tecnologia de implantação abrangente que está incluído no .NET Framework e integra [!INCLUDE[TLA#tla_visualstu](../../../includes/tlasharptla-visualstu-md.md)] (consulte [visão geral da implantação de ClickOnce](https://msdn.microsoft.com/library/142dbbz4.aspx) para obter informações detalhadas). Autônomo [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplicativos podem ser implantados usando [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)], enquanto aplicativos hospedados pelo navegador devem ser implantados com [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)].  
  
 Aplicativos implantados usando [!INCLUDE[TLA2#tla_clickonce](../../../includes/tla2sharptla-clickonce-md.md)] recebem uma camada adicional de segurança ao longo [!INCLUDE[TLA#tla_cas](../../../includes/tlasharptla-cas-md.md)]; basicamente, [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] aplicativos implantados solicitam as permissões que eles precisam. Eles recebem somente as permissões se eles não excedem o conjunto de permissões para a zona da qual o aplicativo é implantado. Ao reduzir o conjunto de permissões para somente aquelas que são necessárias, mesmo que elas sejam menos do que as fornecidas pelo conjunto de permissões da zona de inicialização, o número de recursos aos quais o aplicativo tem acesso é reduzido ao mínimo necessário. Consequentemente, se o aplicativo for sequestrado, o potencial de danos ao computador cliente será reduzido.  
  
<a name="Security_Critical_Methodology"></a>   
### <a name="security-critical-methodology"></a>Metodologia Crítica para Segurança  
 O [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] código que usa permissões para habilitar a área restrita da zona da Internet para [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] aplicativos devem ser mantidos no grau mais alto possível de auditoria de segurança e controle. Para facilitar esse requisito, o .NET Framework fornece o novo suporte para o gerenciamento de código que eleva os privilégios. Especificamente, o [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] permite que você identifique o código que eleva os privilégios e marcá-la com o <xref:System.Security.SecurityCriticalAttribute>; qualquer código não marcado com <xref:System.Security.SecurityCriticalAttribute> se torna *transparente* usando essa metodologia. Por outro lado, código gerenciado que não está marcado com <xref:System.Security.SecurityCriticalAttribute> é impedido de elevar privilégios.  
  
 A metodologia crítica para segurança permite que a organização dos [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] código que eleva os privilégios em *kernel crítico para segurança*, com o restante sendo transparente. Isolar o código crítico para segurança permite que o [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] equipe de engenharia concentre-se um controle de origem e de análise de segurança adicional no kernel crítico para segurança além das práticas de segurança padrão (consulte [estratégia de segurança do WPF -Engenharia de segurança](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)).  
  
 Observe que o .NET Framework permite que código confiável estenda a [!INCLUDE[TLA2#tla_winfxwebapp](../../../includes/tla2sharptla-winfxwebapp-md.md)] área restrita da zona da Internet, permitindo que os desenvolvedores escrevam assemblies gerenciados marcados com <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA) e implantado para do usuário Global Assembly Cache (GAC). Marcar um assembly com um APTCA é uma operação de segurança altamente confidencial, pois permite que qualquer código chame esse assembly, incluindo um código mal-intencionado da Internet. Deve-se ter extremo cuidado e usar as melhores práticas ao fazer isso e os usuários devem optar por confiar nesse software para que ele seja instalado.  
  
<a name="Microsoft_Internet_Explorer_Security"></a>   
## <a name="microsoft-internet-explorer-security"></a>Segurança do Microsoft Internet Explorer  
 Além de reduzir problemas de segurança e simplificar a configuração de segurança [!INCLUDE[TLA#tla_ie6sp2](../../../includes/tlasharptla-ie6sp2-md.md)] contém vários recursos que aprimoram a segurança para usuários de melhorias de segurança [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)]. O foco desses recursos tenta permitir aos usuários um maior controle sobre sua experiência de navegação.  
  
 Antes de [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)], os usuários podiam estar sujeitos a qualquer um dos seguintes:  
  
-   Janelas pop-up aleatórias.  
  
-   Redirecionamento de script confuso.  
  
-   Várias caixas de diálogo de segurança em alguns sites.  
  
 Em alguns casos, sites não confiáveis tentavam enganar os usuários por meio da instalação falsificação [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] ou mostrando repetidas vezes uma [!INCLUDE[TLA#tla_actx](../../../includes/tlasharptla-actx-md.md)] caixa de diálogo de instalação, mesmo que o usuário pudesse ter a cancelado. Usando essas técnicas, é possível que um número significativo de usuários tenha sido levado a tomar decisões erradas que resultaram na instalação de aplicativos spyware.  
  
 O [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] inclui vários recursos para atenuar esses tipos de problemas, que giram em torno do conceito de iniciação pelo usuário. [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] detecta quando um usuário clica em um elemento de link ou página antes de uma ação, que é conhecido como *iniciação pelo usuário*e trata de forma diferente do que uma ação semelhante é disparada por um script em uma página. Por exemplo, [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] incorpora uma **Bloqueador de pop-up** que detecta quando um usuário clica em um botão antes que a página de criação de um pop-up. Isso permite que [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] para permitir pop-ups mais inofensivos evitando pop-ups que os usuários não solicitados nem desejados. Pop-ups bloqueados são interceptados na nova **barra de informações**, que permite que o usuário substitua o bloco manualmente e exibir o pop-up.  
  
 A mesma lógica de iniciação pelo usuário também é aplicada a **aberto**/**salvar** avisos de segurança. As caixas de diálogo de instalação do [!INCLUDE[TLA2#tla_actx](../../../includes/tla2sharptla-actx-md.md)] sempre são interceptadas na Barra de Informações, a menos que elas representem uma atualização de um controle instalado anteriormente. Essas medidas são combinadas para fornecer aos usuários uma experiência do usuário mais segura e mais controlada, já que eles estão protegidos contra sites que os induzem a instalar software indesejado ou mal-intencionado.  
  
 Esses recursos também protegem os clientes que usam [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] para navegar por sites da web que lhes permitem baixar e instalar [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplicativos. Em particular, isso ocorre porque [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] oferece uma melhor experiência de usuário, o que reduz a possibilidade dos usuários instalarem aplicativos mal-intencionados ou desonestos, independentemente de qual tecnologia foi usada para criá-los, incluindo [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] adiciona essas proteções usando [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] para facilitar o download de seus aplicativos pela Internet. Uma vez que [!INCLUDE[TLA#tla_winfxwebapp#plural](../../../includes/tlasharptla-winfxwebappsharpplural-md.md)] executar dentro de uma área de segurança da zona de Internet, podem ser iniciados diretamente. Por outro lado, autônomo [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] aplicativos exigem confiança total para executar. Para esses aplicativos, [!INCLUDE[TLA#tla_clickonce](../../../includes/tlasharptla-clickonce-md.md)] exibirá uma caixa de diálogo de segurança durante o processo de inicialização para notificar o uso dos requisitos de segurança adicionais do aplicativo. No entanto, isso deve ser iniciado pelo usuário, também será regido pela lógica iniciada pelo usuário e pode ser cancelado.  
  
 [!INCLUDE[TLA2#tla_ie7](../../../includes/tla2sharptla-ie7-md.md)] incorpora e estende os recursos de segurança do [!INCLUDE[TLA2#tla_ie6sp2](../../../includes/tla2sharptla-ie6sp2-md.md)] como parte de um compromisso contínuo de segurança.  
  
## <a name="see-also"></a>Consulte também  
 [Noções básicas de segurança do Microsoft Internet Explorer 6 no Windows XP SP2](https://www.microsoft.com/downloads/details.aspx?FamilyId=E550F940-37A0-4541-B5E2-704AB386C3ED&displaylang=en)  
 [Compreendendo e trabalhando no modo protegido do Internet Explorer](https://msdn.microsoft.com/library/bb250462.aspx)  
 [Windows XP Service Pack 3](https://www.microsoft.com/windows/products/windowsxp/sp3/default.mspx)  
 [Guia de segurança do Windows Vista](https://www.microsoft.com/downloads/details.aspx?familyid=a3d1bbed-7f35-4e72-bfb5-b84a526c1565&displaylang=en)  
 [Segurança de acesso do código](../../../docs/framework/misc/code-access-security.md)  
 [Segurança](../../../docs/framework/wpf/security-wpf.md)  
 [Segurança parcialmente confiável do WPF](../../../docs/framework/wpf/wpf-partial-trust-security.md)  
 [Estratégia de segurança do WPF – Engenharia de segurança](../../../docs/framework/wpf/wpf-security-strategy-security-engineering.md)
