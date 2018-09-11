---
title: Estratégia de segurança do WPF - engenharia de segurança
ms.date: 03/30/2017
helpviewer_keywords:
- security [WPF], testing techniques
- Security Development Lifecycle (SDL), security analysis [WPF]
- Security Development Lifecycle (SDL), threat modeling
- Security Development Lifecycle (SDL), testing techniques
- Security Development Lifecycle (SDL), source analysis tools
- Security Development Lifecycle (SDL), critical code management
- threat modeling [WPF]
ms.assetid: 0fc04394-4e47-49ca-b0cf-8cd1161d95b9
ms.openlocfilehash: fd29696d88eba5c1363464334b63cb2ab0df4a0e
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44342624"
---
# <a name="wpf-security-strategy---security-engineering"></a>Estratégia de segurança do WPF - engenharia de segurança
A Computação Confiável é uma iniciativa da Microsoft para garantir a produção de código seguro. Um elemento chave da iniciativa Computação Confiável é o [!INCLUDE[TLA#tla_sdl](../../../includes/tlasharptla-sdl-md.md)]. O [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] é uma prática de engenharia que é usada em conjunto com processos de engenharia padrão para facilitar o fornecimento de código seguro. O [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] consiste em dez fases que combinam melhores práticas com formalização, mensurabilidade e estruturas adicionais, incluindo:  
  
-   Análise de projeto de segurança  
  
-   Verificações de qualidade baseadas em ferramenta  
  
-   Testes de penetração  
  
-   Análise final de segurança  
  
-   Gerenciamento de segurança do produto pós-lançamento  
  
## <a name="wpf-specifics"></a>Aspectos específicos do WPF  
 A equipe de engenharia do [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] aplica e estende o [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)], a combinação dos quais inclui os seguintes aspectos principais:  
  
 [Modelagem de ameaças](#threat_modeling)  
  
 [Ferramentas de edição e análise de segurança](#tools)  
  
 [Técnicas de teste](#techniques)  
  
 [Gerenciamento de código crítico](#critical_code)  
  
<a name="threat_modeling"></a>   
### <a name="threat-modeling"></a>Modelagem de ameaças  
 A modelagem de ameaças é um componente principal do [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] e é usada para criar o perfil de um sistema para determinar potenciais vulnerabilidades de segurança. Após as vulnerabilidades serem identificadas, a modelagem de ameaças também garante que as atenuações apropriadas estejam em vigor.  
  
 De modo geral, a modelagem de ameaças envolve as seguintes etapas principais, usando uma mercearia como exemplo:  
  
1.  **Identificando ativos**. Os ativos de uma mercearia podem incluir funcionários, um cofre, caixas e o inventário.  
  
2.  **Enumerando pontos de entrada**. Os pontos de entrada de uma mercearia podem incluir as portas da frente e de trás, janelas, a estação de carga e as unidades de ar-condicionado.  
  
3.  **Investigando ataques contra ativos usando pontos de entrada**. Um possível ataque poderia ter como alvo o ativo *cofre* de uma mercearia por meio do ponto de entrada *ar-condicionado*; a unidade de ar-condicionado poderia ser removida para permitir que o cofre seja passado por ela e retirado da mercearia.  
  
 A modelagem de ameaças é aplicada no [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] e inclui o seguinte:  
  
-   Como o analisador [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] lê arquivos, mapeia texto para classes de modelo de objeto correspondentes e cria o código real.  
  
-   Como um identificador de janela (hWnd) é criado, envia mensagens e é usado para renderizar o conteúdo de uma janela.  
  
-   Como a vinculação de dados obtém recursos e interage com o sistema.  
  
 Esses modelos de ameaças são importantes para identificar requisitos de design de segurança e reduções de ameaças durante o processo de desenvolvimento.  
  
<a name="tools"></a>   
### <a name="source-analysis-and-editing-tools"></a>Ferramentas de edição e análise de código-fonte  
 Além dos elementos manuais de revisão de código de segurança do [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)], a equipe do [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] usa várias ferramentas para análise do código-fonte e das edições associadas para diminuir as vulnerabilidades de segurança. Uma ampla variedade de ferramentas de código são usadas e incluem o seguinte:  
  
-   **FXCop**: encontra problemas comuns de segurança no código gerenciado, que vão desde as regras de herança ao uso da segurança do acesso de código e a como interoperar com segurança com código não gerenciado. Consulte [FXCop](http://www.gotdotnet.com/team/fxcop/).  
  
-   **Prefix/Prefast**: localiza vulnerabilidades de segurança e problemas comuns de segurança em código não gerenciado, como saturações de buffer, problemas com cadeias de formatação e verificação de erros.  
  
-   **APIs banidas**: pesquisa o código-fonte para identificar usos acidentais de funções que são conhecidas por causar problemas de segurança, como `strcpy`. Após serem identificadas, essas funções são substituídas por alternativas mais seguras.  
  
<a name="techniques"></a>   
### <a name="testing-techniques"></a>Técnicas de teste  
 O [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] usa uma variedade de técnicas teste de segurança que incluem:  
  
-   **Testes caixa branca**: os testadores exibem o código-fonte e, em seguida, criam testes de falhas  
  
-   **Testes caixa preta**: os testadores tentam localizar falhas de segurança examinando as API e os recursos e, em seguida, tentam atacar o produto.  
  
-   **Regressão de problemas de segurança de outros produtos**: quando for relevante, problemas de segurança de produtos relacionados serão testados. Por exemplo, variantes apropriadas de cerca de sessenta problemas de segurança para [!INCLUDE[TLA2#tla_ie](../../../includes/tla2sharptla-ie-md.md)] foram identificadas e sua aplicabilidade foi testada para [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
-   **Testes de penetração baseados em ferramentas por meio de fuzzing de arquivos**: fuzzing de arquivos é a exploração do intervalo de entradas de um leitor de arquivos por meio de uma variedade de entradas. Um exemplo de uso dessa técnica no [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] é para verificar se há falhas no código de decodificação de imagens.  
  
<a name="critical_code"></a>   
### <a name="critical-code-management"></a>Gerenciamento de código crítico  
 Para [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] baseia-se uma proteção de segurança, usando o suporte do .NET Framework para marcar e acompanhar o código de segurança crítica que elevam privilégios (consulte **metodologia crítica para segurança** em [WPF Estratégia de segurança – segurança da plataforma](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)). Considerando os altos requisitos de qualidade da segurança em códigos críticos para a segurança, esse código recebe um nível adicional de auditoria de segurança e controle de gerenciamento de código-fonte. Aproximadamente 5% a 10% do [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] consiste em código crítico para a segurança, que é revisado por uma equipe de revisão dedicada. O código-fonte e o processo de check-in são gerenciados acompanhando o código crítico para segurança e mapeando cada entidade crítica (isto é, um método que contém código crítico) quanto ao seu estado de aprovação. O estado de aprovação inclui os nomes de um ou mais revisores. Cada build diária de [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] compara o código crítico com o dos builds anteriores para verificar se há alterações não aprovadas. Se um engenheiro modificar o código crítico sem a aprovação da equipe de revisão, isso será identificado e corrigido imediatamente. Esse processo permite a aplicação e a manutenção de um nível especialmente alto de investigação do código na área restrita [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
## <a name="see-also"></a>Consulte também  
 [Segurança](../../../docs/framework/wpf/security-wpf.md)  
 [Segurança parcialmente confiável do WPF](../../../docs/framework/wpf/wpf-partial-trust-security.md)  
 [Estratégia de segurança do WPF – segurança da plataforma](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)  
 [Computação confiável](https://www.microsoft.com/mscorp/twc/default.mspx)  
 [Modelagem de ameaças de aplicativos](https://msdn.microsoft.com/security/securecode/threatmodeling/acetm/)  
 [Diretrizes de segurança: .NET Framework 2.0](https://msdn.microsoft.com/library/default.asp?url=/library/dnpag2/html/PAGGuidelines0003.asp)
