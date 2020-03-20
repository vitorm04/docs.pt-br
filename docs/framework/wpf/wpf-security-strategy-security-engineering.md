---
title: Estratégia de segurança e engenharia
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
ms.openlocfilehash: 970627c5de4964ebd5331c488152022fda55bd74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174557"
---
# <a name="wpf-security-strategy---security-engineering"></a>Estratégia de segurança do WPF - engenharia de segurança
A Computação Confiável é uma iniciativa da Microsoft para garantir a produção de código seguro. Um elemento-chave da iniciativa De Computação Confiável é o SDL (Microsoft Security Development Lifecycle, ciclo de vida de desenvolvimento de segurança) da Microsoft. O SDL é uma prática de engenharia que é usada em conjunto com processos de engenharia padrão para facilitar a entrega de código seguro. O SDL consiste em dez fases que combinam as melhores práticas com formalização, mensurabilidade e estrutura adicional, incluindo:  
  
- Análise de projeto de segurança  
  
- Verificações de qualidade baseadas em ferramenta  
  
- Testes de penetração  
  
- Análise final de segurança  
  
- Gerenciamento de segurança do produto pós-lançamento  
  
## <a name="wpf-specifics"></a>Aspectos específicos do WPF  
 A [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] equipe de engenharia aplica e estende o SDL, a combinação que inclui os seguintes aspectos-chave:  
  
 [Modelagem de ameaças](#threat_modeling)  
  
 [Ferramentas de edição e análise de segurança](#tools)  
  
 [Técnicas de teste](#techniques)  
  
 [Gerenciamento de código crítico](#critical_code)  
  
<a name="threat_modeling"></a>
### <a name="threat-modeling"></a>Modelagem de ameaças  
 A modelagem de ameaças é um componente central do SDL e é usada para traçar um perfil de um sistema para determinar possíveis vulnerabilidades de segurança. Após as vulnerabilidades serem identificadas, a modelagem de ameaças também garante que as atenuações apropriadas estejam em vigor.  
  
 De modo geral, a modelagem de ameaças envolve as seguintes etapas principais, usando uma mercearia como exemplo:  
  
1. **Identificando ativos**. Os ativos de uma mercearia podem incluir funcionários, um cofre, caixas e o inventário.  
  
2. **Enumerando pontos de entrada**. Os pontos de entrada de uma mercearia podem incluir as portas da frente e de trás, janelas, a estação de carga e as unidades de ar-condicionado.  
  
3. **Investigando ataques contra ativos usando pontos de entrada**. Um possível ataque poderia ter como alvo o ativo *cofre* de uma mercearia por meio do ponto de entrada *ar-condicionado*; a unidade de ar-condicionado poderia ser removida para permitir que o cofre seja passado por ela e retirado da mercearia.  
  
 A modelagem de ameaças é aplicada no [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] e inclui o seguinte:  
  
- Como o analisador [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] lê arquivos, mapeia texto para classes de modelo de objeto correspondentes e cria o código real.  
  
- Como um identificador de janela (hWnd) é criado, envia mensagens e é usado para renderizar o conteúdo de uma janela.  
  
- Como a vinculação de dados obtém recursos e interage com o sistema.  
  
 Esses modelos de ameaças são importantes para identificar requisitos de design de segurança e reduções de ameaças durante o processo de desenvolvimento.  
  
<a name="tools"></a>
### <a name="source-analysis-and-editing-tools"></a>Ferramentas de edição e análise de código-fonte  
 Além dos elementos de revisão manual do código [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] de segurança do SDL, a equipe usa várias ferramentas para análise de origem e edições associadas para diminuir as vulnerabilidades de segurança. Uma ampla variedade de ferramentas de código são usadas e incluem o seguinte:  
  
- **FXCop**: encontra problemas comuns de segurança no código gerenciado, que vão desde as regras de herança ao uso da segurança do acesso de código e a como interoperar com segurança com código não gerenciado. Consulte [FXCop](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/bb429476%28v=vs.80%29).  
  
- **Prefix/Prefast**: localiza vulnerabilidades de segurança e problemas comuns de segurança em código não gerenciado, como saturações de buffer, problemas com cadeias de formatação e verificação de erros.  
  
- **APIs banidas**: pesquisa o código-fonte para identificar usos acidentais de funções que são conhecidas por causar problemas de segurança, como `strcpy`. Uma vez identificadas, essas funções são substituídas por alternativas mais seguras.  
  
<a name="techniques"></a>
### <a name="testing-techniques"></a>Técnicas de teste  
 O [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] usa uma variedade de técnicas teste de segurança que incluem:  
  
- **Whitebox Testing**: Os testadores visualizam o código-fonte e, em seguida, constroem testes de exploração.
  
- **Testes caixa preta**: os testadores tentam localizar falhas de segurança examinando as API e os recursos e, em seguida, tentam atacar o produto.  
  
- **Regressão de problemas de segurança de outros produtos**: quando for relevante, problemas de segurança de produtos relacionados serão testados. Por exemplo, variantes apropriadas de aproximadamente sessenta problemas de segurança para [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]o Internet Explorer foram identificadas e testadas para sua aplicabilidade a .  
  
- **Testes de penetração baseados em ferramentas por meio de fuzzing de arquivos**: fuzzing de arquivos é a exploração do intervalo de entradas de um leitor de arquivos por meio de uma variedade de entradas. Um exemplo de uso dessa técnica no [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] é para verificar se há falhas no código de decodificação de imagens.  
  
<a name="critical_code"></a>
### <a name="critical-code-management"></a>Gerenciamento de código crítico  
 Para xbaps (XBAPs), [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] os aplicativos do navegador XAML constroem uma caixa de areia de segurança usando o suporte ao .NET Framework para marcar e rastrear códigos críticos de segurança que elevem privilégios (consulte Metodologia De Segurança Crítica na Estratégia **de** Segurança do [WPF - Segurança da Plataforma](wpf-security-strategy-platform-security.md)). Considerando os altos requisitos de qualidade da segurança em códigos críticos para a segurança, esse código recebe um nível adicional de auditoria de segurança e controle de gerenciamento de código-fonte. Aproximadamente 5% a 10% do [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] consiste em código crítico para a segurança, que é revisado por uma equipe de revisão dedicada. O código-fonte e o processo de check-in são gerenciados acompanhando o código crítico para segurança e mapeando cada entidade crítica (isto é, um método que contém código crítico) quanto ao seu estado de aprovação. O estado de aprovação inclui os nomes de um ou mais revisores. Cada build diária de [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] compara o código crítico com o dos builds anteriores para verificar se há alterações não aprovadas. Se um engenheiro modificar o código crítico sem a aprovação da equipe de revisão, isso será identificado e corrigido imediatamente. Esse processo permite a aplicação e a manutenção de um nível especialmente alto de investigação do código na área restrita [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
## <a name="see-also"></a>Confira também

- [Segurança](security-wpf.md)
- [Segurança parcial de confiança do WPF](wpf-partial-trust-security.md)
- [Estratégia de segurança do WPF - segurança da plataforma](wpf-security-strategy-platform-security.md)
- [Computação Confiável](https://www.microsoft.com/mscorp/twc/default.mspx)
- [Segurança no .NET](../../standard/security/index.md)
