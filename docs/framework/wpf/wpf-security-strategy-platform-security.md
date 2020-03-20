---
title: Estratégia de segurança da plataforma
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
ms.openlocfilehash: 258fcd7c51ea59de03fe60a4eeb9a82dd1c7efca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174596"
---
# <a name="wpf-security-strategy---platform-security"></a>Estratégia de segurança do WPF - segurança da plataforma
Embora o Windows Presentation Foundation (WPF) forneça uma variedade de serviços de segurança, ele também aproveita os recursos de segurança da plataforma subjacente, que inclui o sistema operacional, o CLR e o Internet Explorer. Essas camadas combinam-se para fornecer ao WPF um modelo de segurança forte e de defesa em profundidade que tenta evitar qualquer ponto de falha, como mostrado na figura a seguir:  
  
 ![Diagrama que mostra o modelo de segurança WPF.](./media/wpf-security-strategy-platform-security/windows-presentation-foundation-security.png)  
  
 O restante deste tópico discute os recursos em cada uma dessas camadas que pertencem especificamente ao WPF.  

## <a name="operating-system-security"></a>Segurança do sistema operacional  
O núcleo do Windows fornece vários recursos de segurança que formam a base de segurança para todos os aplicativos windows, incluindo aqueles construídos com WPF. Este tópico discute a amplitude desses recursos de segurança que são importantes para o WPF, bem como como o WPF se integra com eles para fornecer mais defesa em profundidade.  
  
### <a name="microsoft-windows-xp-service-pack-2-sp2"></a>SP2 (Microsoft Windows XP Service Pack 2)  
 Além de uma revisão geral e fortalecimento do Windows, existem três recursos principais do Windows XP SP2 que discutiremos neste tópico:  
  
- Compilação com /GS  
  
- Atualização do Microsoft Windows.  
  
#### <a name="gs-compilation"></a>Compilação com /GS  
 O Windows XP SP2 oferece proteção recompilando muitas bibliotecas principais do sistema, incluindo todas as dependências do WPF, como a CLR, para ajudar a mitigar os excessos de buffer. Isso é feito pelo uso do parâmetro /GS com o compilador de linha de comando C/C++. Embora seja necessário evitar estouros de buffer explicitamente, a compilação com /GS fornece um exemplo de uma proteção extensa contra possíveis vulnerabilidades que são criadas de maneira inadvertida ou mal-intencionada por eles.  
  
 Historicamente, os estouros de buffer tem sido a causa de diversas explorações de segurança de alto impacto. Um estouro de buffer ocorre quando um invasor aproveita uma vulnerabilidade de código que permite a injeção de um código mal-intencionado escrito além dos limites de um buffer. Em seguida, isso permite que um invasor sequestre o processo no qual o código está em execução, substituindo o endereço de retorno de uma função para fazer com que o código do invasor seja executado. O resultado é um código mal-intencionado que executa um código arbitrário com os mesmos privilégios do processo sequestrado.  
  
 Em um nível alto, o sinalizador do compilador -GS protege contra alguns potenciais excessos de buffer, injetando um cookie de segurança especial para proteger o endereço de retorno de uma função que tem buffers de string locais. Após o retorno de uma função, o cookie de segurança é comparado com seu valor anterior. Se o valor tiver sido alterado, poderá ter ocorrido um estouro de buffer e o processo será interrompido com uma condição de erro. A interrupção do processo impede a execução do código potencialmente mal-intencionado. Consulte [-GS (Buffer Security Check)](/cpp/build/reference/gs-buffer-security-check) para obter mais detalhes.  
  
 O WPF é compilado com o sinalizador /GS para adicionar mais uma camada de defesa aos aplicativos WPF.  
  
### <a name="windows-vista"></a>Windows Vista  
Os usuários do WPF no Windows Vista se beneficiarão dos aprimoramentos adicionais de segurança do sistema operacional, incluindo "Acesso ao Usuário menos privilegiado", verificações de integridade de código e isolamento de privilégios.  
  
#### <a name="user-account-control-uac"></a>UAC (Controle de Conta de Usuário)  
 Hoje, os usuários do Windows tendem a ser executados com privilégios de administrador porque muitos aplicativos exigem que eles sejam instalados ou executados, ou ambos. Ter a capacidade de escrever configurações de aplicativo padrão no Registro é um exemplo.  
  
 De fato, a execução com privilégios de administrador significa que os aplicativos são executados em processos que receberam privilégios de administrador. O impacto de segurança disto é que qualquer código mal-intencionado que sequestre um processo executado com privilégios de administrador herdará automaticamente esses privilégios, incluindo o acesso a recursos críticos do sistema.  
  
 Uma maneira de se proteger contra essa ameaça de segurança é executar aplicativos com o mínimo de privilégios necessários. Isso é conhecido como o princípio do menor privilégio, e é uma característica central do sistema operacional Windows. Esse recurso é chamado de Controle de Conta de Usuário (UAC), e é usado pelo Windows UAC de duas maneiras principais:  
  
- Para executar a maioria dos aplicativos com privilégios UAC por padrão, mesmo se o usuário for um administrador; somente os aplicativos que precisam de privilégios de administrador serão executados com privilégios de administrador. Para serem executados com privilégios administrativos, os aplicativos devem ser explicitamente marcados em seus manifestos do aplicativo ou como uma entrada na política de segurança.  
  
- Para fornecer soluções de compatibilidade como virtualização. Por exemplo, vários aplicativos tentam gravar em localizações restritas como C:\Program Files. Para os aplicativos executados no UAC, existe uma localização alternativa por usuário que não exige privilégios de administrador para ser usada para gravação. Para os aplicativos executados no UAC, o UAC virtualiza C:\Program Files para que os aplicativos que acreditam que estão fazendo gravações nele, na verdade, estão gravando na localização alternativa por usuário. Esse tipo de trabalho de compatibilidade permite que o sistema operacional execute vários aplicativos que anteriormente não podiam ser executados no UAC.  
  
#### <a name="code-integrity-checks"></a>Verificações de integridade de código  
 O Windows Vista incorpora verificações mais profundas de integridade de código para ajudar a evitar que o código malicioso seja injetado em arquivos do sistema ou no kernel no tempo de carga/execução. Isso vai além da proteção de arquivo do sistema.  

### <a name="limited-rights-process-for-browser-hosted-applications"></a>Processos com direitos limitados para aplicativos hospedados pelo navegador  
 Os aplicativos WPF hospedados no navegador são executados na caixa de areia da região da Internet. A integração do WPF com o Microsoft Internet Explorer estende essa proteção com suporte adicional.  
  
 Uma vez que os aplicativos de navegador XAML (XBAPs) são geralmente sandboxed pelo conjunto de permissões de zona da Internet, remover esses privilégios não prejudica os aplicativos do navegador XAML (XBAPs) de uma perspectiva de compatibilidade. Em vez disso, é criada uma camada adicional de proteção extensa; se um aplicativo em área restrita puder explorar outras camadas e sequestrar o processo, ainda assim, o processo apenas terá privilégios limitados.  
  
 Consulte [Usando uma conta de usuário menos privilegiada.](https://docs.microsoft.com/previous-versions/tn-archive/cc700846%28v=technet.10%29)  
  
## <a name="common-language-runtime-security"></a>Segurança do Common Language Runtime  
 O tempo de execução do idioma comum (CLR) oferece uma série de benefícios importantes de segurança que incluem validação e verificação, CAS (Code Access Security) e a Metodologia Crítica de Segurança.  

### <a name="validation-and-verification"></a>Validação e verificação  
 Para proporcionar isolamento e integridade da montagem, a CLR utiliza um processo de validação. A validação do CLR garante que os conjuntos sejam isolados validando o formato de arquivo Executável Portátil (PE) para endereços que apontam fora do conjunto. A validação do CLR também valida a integridade dos metadados incorporados em um conjunto.  
  
 Para garantir a segurança do tipo, ajudar a evitar problemas comuns de segurança (por exemplo, buffer overruns), e permitir o sandboxing através do isolamento do subprocesso, a segurança clr usa o conceito de verificação.  
  
 Os aplicativos gerenciados são compilados em MSIL (Microsoft Intermediate Language). Quando os métodos em um aplicativo gerenciado são executados, a MSIL é compilada em código nativo por meio da compilação JIT (Just-In-Time). A compilação JIT inclui um processo de verificação que aplica várias regras de segurança e robustez que garantem que o código não:  
  
- Viola contratos de tipos  
  
- Introduz estouros de buffer  
  
- Acessa a memória de forma ampla.  
  
 O código gerenciado que não está em conformidade com as regras de verificação não tem permissão de ser executado, a menos que seja considerado um código confiável.  
  
 A vantagem do código verificável é uma das principais razões pelas quais o WPF se baseia no Quadro .NET. Na medida em que um código verificável é usado, a possibilidade de exploração de possíveis vulnerabilidades é consideravelmente reduzida.  
  
### <a name="code-access-security"></a>Segurança de Acesso do Código  
 Um computador cliente expõe uma grande variedade de recursos aos quais um aplicativo gerenciado pode ter acesso, incluindo o sistema de arquivos, o Registro, serviços de impressão, a interface do usuário, reflexão e variáveis de ambiente. Antes que um aplicativo gerenciado possa acessar qualquer um dos recursos em uma máquina cliente, ele deve ter permissão .NET Framework para fazê-lo. Uma permissão no CAS é <xref:System.Security.CodeAccessPermission>uma subclasse do; O CAS implementa uma subclasse para cada recurso que os aplicativos gerenciados podem acessar.  
  
 O conjunto de permissões que um aplicativo gerenciado é concedido pelo CAS quando ele começa a ser executado é conhecido como um conjunto de permissões e é determinado por evidências fornecidas pelo aplicativo. Para aplicações WPF, a evidência fornecida é a localização ou zona, a partir da qual os aplicativos são lançados. O CAS identifica as seguintes zonas:  
  
- **Meu computador.** Aplicativos iniciados no computador cliente (Totalmente Confiável).  
  
- **Intranet local**. Aplicativos iniciados na intranet. (Um Pouco Confiáveis).  
  
- **Internet**. Aplicativos iniciados na Internet. (Os Menos Confiáveis).  
  
- **Sites confiáveis**. Aplicativos identificados por um usuário como sendo confiáveis. (Os Menos Confiáveis).  
  
- **Sites não confiáveis**. Aplicativos identificados por um usuário como sendo não confiáveis. (Não Confiáveis).  
  
 Para cada uma dessas regiões, o CAS fornece um conjunto de permissões predefinido que inclui as permissões que correspondem ao nível de confiança associado a cada um. Eles incluem:  
  
- **FullTrust**. Para aplicações lançadas a partir da região **Meu Computador.** Todas as permissões possíveis são concedidas.  
  
- **LocalIntranet**. Para aplicações lançadas a partir da região **Intranet Local.** Um subconjunto de permissões é concedido para fornecer acesso moderado aos recursos do computador cliente, incluindo armazenamento isolado, acesso irrestrito à interface do usuário, caixas de diálogo de arquivo irrestritas, reflexão limitada e acesso limitado a variáveis de ambiente. Permissões para recursos críticos, como o Registro, não são fornecidas.  
  
- **Internet**. Para aplicativos lançados da região **da Internet** ou **sites confiáveis.** Um subconjunto de permissões é concedido para permitir acesso limitado aos recursos do computador cliente, incluindo armazenamento isolado, somente abertura de arquivo e interface do usuário limitada. Essencialmente, este conjunto de permissões isola os aplicativos da máquina cliente.  
  
 Os aplicativos identificados como sendo da região **Sites não confiáveis** não recebem nenhuma permissão do CAS. Consequentemente, não existe um conjunto de permissões predefinidas para eles.  
  
 A figura a seguir ilustra a relação entre zonas, conjuntos de permissões, permissões e recursos:  
  
 ![Diagrama que mostra conjuntos de permissões CAS.](./media/wpf-security-strategy-platform-security/code-access-security-permissions-relationship.png)  
  
 As restrições da caixa de areia de segurança da zona da Internet se aplicam igualmente a qualquer código que um XBAP importa de uma biblioteca de sistemas, incluindo o WPF. Isso garante que cada pedaço do código seja bloqueado, até mesmo o WPF. Infelizmente, para ser capaz de executar, um XBAP precisa executar uma funcionalidade que requer mais permissões do que as habilitadas pela caixa de areia de segurança da região da Internet.  
  
 Considere um aplicativo XBAP que inclui a seguinte página:  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 Para executar este XBAP, o código WPF subjacente deve executar mais funcionalidade do que está disponível para a chamada XBAP, incluindo:  
  
- Criando uma alça de janela (HWND) para renderização  
  
- Expedição de mensagens  
  
- Carregamento da fonte Tahoma  
  
 De um ponto de vista de segurança, permitir o acesso direto a qualquer uma dessas operações pelo aplicativo em área restrita seria catastrófico.  
  
 Felizmente, o WPF atende a essa situação, permitindo que essas operações sejam executadas com privilégios elevados em nome do aplicativo sandboxed. Enquanto todas as operações wpf são verificadas contra as permissões limitadas de segurança da zona de Internet do domínio de aplicativo do XBAP, o WPF (como em outras bibliotecas do sistema) recebe um conjunto de permissões que inclui todas as permissões possíveis.
  
 Isso exige que o WPF receba privilégios elevados, evitando que esses privilégios sejam regidos pelo conjunto de permissões da região da Internet do domínio do aplicativo host.  
  
 O WPF faz isso usando o método **Assert** de uma permissão. O código a seguir mostra como isso acontece.  
  
 [!code-csharp[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/CSharp/Page1.xaml.cs#permission)]
 [!code-vb[WPFPlatformSecuritySnippets#Permission](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFPlatformSecuritySnippets/VisualBasic/Page1.xaml.vb#permission)]  
  
 O **Assert** essencialmente impede que as permissões ilimitadas exigidas pelo WPF sejam restringidas pelas permissões de zona de Internet do XBAP.  
  
 Do ponto de vista da plataforma, o WPF é responsável por usar **o Assert** corretamente; um uso incorreto do **Assert** poderia permitir que o código malicioso eleve privilégios. Consequentemente, é importante, então, apenas ligar para **o Assert** quando necessário, e garantir que as restrições da caixa de areia permaneçam intactas. Por exemplo, um código em área restrita não tem permissão para abrir arquivos aleatórios, mas tem permissão para usar fontes. O WPF permite que aplicativos sandboxed usem a funcionalidade da fonte ligando para **AAssert**e para o WPF ler arquivos conhecidos para conter essas fontes em nome do aplicativo sandboxed.  
  
### <a name="clickonce-deployment"></a>Implantação do ClickOnce  
 ClickOnce é uma tecnologia de implantação abrangente que está incluída no .NET Framework e se integra ao Visual Studio (consulte [segurança e implantação do ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) para obter informações detalhadas). Os aplicativos WPF autônomos podem ser implantados usando o ClickOnce, enquanto os aplicativos hospedados no navegador devem ser implantados com o ClickOnce.  
  
 Os aplicativos implantados usando o ClickOnce recebem uma camada de segurança adicional sobre o Cas (Code Access Security); essencialmente, os aplicativos implantados ClickOnce solicitam as permissões de que precisam. Eles recebem somente as permissões se eles não excedem o conjunto de permissões para a zona da qual o aplicativo é implantado. Ao reduzir o conjunto de permissões apenas para aqueles que são necessários, mesmo que sejam inferiores às fornecidas pelo conjunto de permissões da zona de lançamento, o número de recursos aos os que o aplicativo tem acesso é reduzido a um mínimo. Consequentemente, se o aplicativo for sequestrado, o potencial de danos ao computador cliente será reduzido.  
  
### <a name="security-critical-methodology"></a>Metodologia Crítica para Segurança  
 O código WPF que usa permissões para habilitar a caixa de areia da região da Internet para aplicativos XBAP deve ser mantido no mais alto grau possível de auditoria e controle de segurança. Para facilitar essa exigência, o .NET Framework fornece um novo suporte para o gerenciamento de código que eleva o privilégio. Especificamente, o CLR permite identificar código que eleve <xref:System.Security.SecurityCriticalAttribute>o privilégio e marcá-lo com o ; qualquer código não <xref:System.Security.SecurityCriticalAttribute> marcado torna-se *transparente* usando esta metodologia. Por outro lado, o código <xref:System.Security.SecurityCriticalAttribute> gerenciado que não está marcado é impedido de elevar o privilégio.  
  
 A Metodologia Security-Critical permite a organização do código WPF que eleva o privilégio em *núcleo crítico de segurança,* com o restante sendo transparente. Isolar o código crítico de segurança permite que a equipe de engenharia do WPF concentre uma análise de segurança adicional e controle de origem no kernel crítico de segurança acima e além das práticas de segurança padrão (ver [Estratégia de Segurança WPF - Engenharia de Segurança](wpf-security-strategy-security-engineering.md)).  
  
 Observe que o .NET Framework permite que o código confiável amplie a caixa de areia da <xref:System.Security.AllowPartiallyTrustedCallersAttribute> zona de Internet XBAP, permitindo que os desenvolvedores escrevam conjuntos gerenciados marcados com (APTCA) e implantados no GAC (Global Assembly Cache, cache de montagem global) do usuário. Marcar um assembly com um APTCA é uma operação de segurança altamente confidencial, pois permite que qualquer código chame esse assembly, incluindo um código mal-intencionado da Internet. Deve-se ter extremo cuidado e usar as melhores práticas ao fazer isso e os usuários devem optar por confiar nesse software para que ele seja instalado.  
  
## <a name="microsoft-internet-explorer-security"></a>Segurança do Microsoft Internet Explorer  
 Além de reduzir problemas de segurança e simplificar a configuração de segurança, o Microsoft Internet Explorer 6 (SP2) contém vários recursos que melhoram a segurança dos usuários de aplicativos de navegador XAML (XBAPs). O foco desses recursos tenta permitir aos usuários um maior controle sobre sua experiência de navegação.  
  
 Antes do IE6 SP2, os usuários podiam estar sujeitos a qualquer um dos seguintes:  
  
- Janelas pop-up aleatórias.  
  
- Redirecionamento de script confuso.  
  
- Várias caixas de diálogo de segurança em alguns sites.  
  
 Em alguns casos, sites não confiáveis tentariam [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] enganar os usuários falsificando a instalação ou mostrando repetidamente uma caixa de diálogo de instalação do Microsoft ActiveX, mesmo que o usuário possa tê-la cancelado. Usando essas técnicas, é possível que um número significativo de usuários tenha sido levado a tomar decisões erradas que resultaram na instalação de aplicativos spyware.  
  
 O IE6 SP2 inclui vários recursos para mitigar esses tipos de problemas, que giram em torno do conceito de iniciação do usuário. O IE6 SP2 detecta quando um usuário clica em um link ou elemento de página antes de uma ação, que é conhecido como iniciação do *usuário,* e o trata de forma diferente do que quando uma ação semelhante é acionada pelo script em uma página. Como exemplo, o IE6 SP2 incorpora um **bloqueador pop-up** que detecta quando um usuário clica em um botão antes da página criar um pop-up. Isso permite que o IE6 SP2 permita pop-ups mais inócuos, evitando pop-ups que os usuários não pedem nem querem. Os pop-ups bloqueados estão presos a nova **Barra de Informações**, que permite ao usuário substituir manualmente o bloco e visualizar o pop-up.  
  
 A mesma lógica de iniciação do usuário também é aplicada às solicitações de segurança **Open**/**Save.** As caixas de diálogo de instalação do ActiveX estão sempre presas a Barra de Informações, a menos que representem uma atualização de um controle instalado anteriormente. Essas medidas são combinadas para fornecer aos usuários uma experiência do usuário mais segura e mais controlada, já que eles estão protegidos contra sites que os induzem a instalar software indesejado ou mal-intencionado.  
  
 Esses recursos também protegem os clientes que usam o IE6 SP2 para navegar em sites que permitem baixar e instalar aplicativos WPF. Em particular, isso acontece porque o IE6 SP2 oferece uma melhor experiência ao usuário que reduz a chance de os usuários instalarem aplicativos maliciosos ou desonestos, independentemente de qual tecnologia foi usada para construí-lo, incluindo o WPF. O WPF adiciona a essas proteções usando o ClickOnce para facilitar o download de seus aplicativos pela Internet. Uma vez que os aplicativos do navegador XAML (XBAPs) são executados dentro de uma caixa de areia de segurança da zona da Internet, eles podem ser lançados perfeitamente. Por outro lado, os aplicativos Autônomos WPF exigem total confiança para serem executados. Para esses aplicativos, o ClickOnce exibirá uma caixa de diálogo de segurança durante o processo de lançamento para notificar o uso dos requisitos adicionais de segurança do aplicativo. No entanto, isso deve ser iniciado pelo usuário, também será regido pela lógica iniciada pelo usuário e pode ser cancelado.  
  
 O Internet Explorer 7 incorpora e amplia os recursos de segurança do IE6 SP2 como parte de um compromisso contínuo com a segurança.  
  
## <a name="see-also"></a>Confira também

- [Segurança de acesso a código](../misc/code-access-security.md)
- [Segurança](security-wpf.md)
- [Segurança parcial de confiança do WPF](wpf-partial-trust-security.md)
- [Estratégia de segurança do WPF – Engenharia de segurança](wpf-security-strategy-security-engineering.md)
