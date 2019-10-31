---
title: Comentários da Comunidade do WPF
ms.date: 03/01/2018
helpviewer_keywords:
- community resources [WPF]
- forums [WPF]
- bug descriptions [WPF]
ms.assetid: 468b060a-d54b-4900-a74a-9faccb554045
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ebeae3e51cedd3add2de4062c8914693ac94f7b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73196999"
---
# <a name="wpf-community-feedback"></a>Comentários da Comunidade do WPF

A Microsoft expõe uma variedade de recursos da Comunidade para você aprender sobre, discutir e fornecer comentários sobre o Windows Presentation Foundation (WPF). Esses recursos incluem fóruns e o site [da comunidade de desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/) . Cada recurso da comunidade oferece um conjunto diferente de benefícios. Esses benefícios são descritos aqui, como um conjunto de práticas recomendadas para o uso de cada um para garantir a melhor resposta da Comunidade em uma grande e na Microsoft em particular.

> [!NOTE]
> Não use a seção de comentários localizada na parte inferior de cada página para enviar comentários sobre o produto. Esses links são apenas para comentários sobre a documentação.

## <a name="forums"></a>Fóruns

O [Fórum do WPF](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=wpf) é o principal recurso da Comunidade para discutir e resolver problemas. Os fóruns facilitam a discussão e a resolução de problemas, oferecendo um conjunto abrangente de recursos de suporte que incluem:

- Pesquisa.
- Acompanhamento de discussão.
- Formatação avançada de texto e código.
- Integração com o Visual Studio.
- Envolvimento da comunidade e MVP (Most Valued Professional).
- Monitoramento para assegurar que as postagens sejam respondidas o mais rápido possível.

Outra opção para fazer perguntas para a Comunidade sobre o WPF é [Stack Overflow](https://stackoverflow.com/questions/tagged/wpf).

### <a name="forum-best-practices"></a>Práticas recomendadas de fórum

O uso das práticas recomendadas a seguir ajuda a resolver os problemas postados no fórum do WPF no tempo mais rápido possível. Estas práticas são aplicáveis a todos os fóruns.

#### <a name="search-existing-posts"></a>Pesquisar postagens existentes

Alguns problemas ocorrem com tanta frequência que outros já os enfrentaram antes de você. Consequentemente, você pode resolver o problema rapidamente ou pode adicionar suas informações em uma discussão existente.

#### <a name="use-meaningful-titles"></a>Usar títulos significativos

Títulos concisos e significativos melhoram a descoberta de suas postagens. Eles também facilitam que outros membros da Comunidade do fórum do WPF determinem se podem resolver o problema.

#### <a name="include-appropriate-content"></a>Incluir conteúdo apropriado

Descreva o problema e como você tentou trabalhar com ele. Se possível, inclua snippets de código de suporte ou o exemplo mais simples possível que demonstre o seu problema. Todos esses detalhes ajudam a aumentar a chance de que sua pergunta seja respondida rapidamente.

## <a name="visual-studio-developer-community"></a>Comunidade de Desenvolvedores do Visual Studio

Às vezes, os problemas podem ser difíceis de resolver ou podem ser insolúveis. Essas situações ocorrem devido a bugs na tecnologia, dificuldades em aplicar a tecnologia a cenários específicos ou à falta de suporte para cenários específicos. Essas informações são importantes para a Microsoft e podem ser fornecidas por meio do site [da comunidade de desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/) .

Os itens postados no centro de comentários do produto WPF são roteados para o banco de dados interno de bugs da equipe do WPF. Consequentemente, é a maneira mais confiável de obter seus comentários para o proprietário do recurso do WPF. Além disso, você pode validar e controlar sugestões e bugs, bem como votar neles, o que ajuda a equipe do WPF a priorizar problemas.

### <a name="developer-community-best-practices"></a>Práticas recomendadas da comunidade de desenvolvedores

Ao postar na Comunidade de desenvolvedores do Visual Studio, Pesquisar postagens existentes, fornecer um título significativo e conteúdo apropriado são práticas recomendadas importantes, assim como no caso de postagens no fórum do WPF. Abaixo estão melhores práticas adicionais que você também deve empregar.

#### <a name="search-existing-posts"></a>Pesquisar postagens existentes

Alguns problemas ocorrem com tanta frequência que outros já os enfrentaram antes de você. Consequentemente, você pode resolver seu problema rapidamente ou pode adicionar sua entrada a um problema existente.

#### <a name="use-meaningful-titles"></a>Usar títulos significativos

Títulos concisos e significativos aumentam a chance de que seu problema seja direcionado para a equipe do WPF mais apropriada no menor período de tempo. Isso é particularmente importante para uma tecnologia como o WPF, que contém muitos recursos inter-relacionados.

#### <a name="describe-how-to-reproduce-your-bug"></a>Descrever como reproduzir seu bug

Quando você posta a respeito de um bug, é importante incluir o seguinte nos locais relevantes:

- Forneça uma descrição clara do bug.
- Use snippets de código para dar suporte à descrição do bug.
- Forneça uma lista de etapas que demonstram como reproduzir o bug.
- Inclua o menor exemplo de código possível que reproduza o bug.
- Mencione se o bug é consistentemente reproduzível ou não.
- Inclua informações de exceção relevantes.

 Se o bug for relacionado à instalação ou à configuração, anexe os logs e instantâneos de instalação relevantes (arquivos prefixados com "dd _" que estão localizados na sua pasta %temp%).

 Para problemas relacionados ao build ou a compilação, anexe os logs de build. O sistema MSBuild pode ser configurado para dar suporte ao registro em log com vários verbosities usando a opção/v: da linha de comando ou configurando o nível apropriado de um ambiente de desenvolvimento integrado (IDE) como o Visual Studio.

#### <a name="provide-environment-information"></a>Fornecer informações de ambiente

Informações básicas geralmente podem ser úteis para adicionar contexto à sua postagem. Em particular, mencione a plataforma do sistema operacional, família de processadores e arquitetura, como "Windows 10 versão 1709, Intel (R) Xeon (R), x64".

Se o problema sobre o qual você está postando está relacionado à renderização, inclua também detalhes da placa e do driver de elementos gráficos, se possível. Essas informações são importantes porque o WPF é uma estrutura de apresentação.

#### <a name="provide-solution-or-project-information"></a>Fornecer informações sobre a solução ou o projeto

Os bugs podem pertencer às ferramentas usadas para desenvolver e compilar seus aplicativos e aos tipos de aplicativos que você está compilando. Consequentemente, pode ser útil especificar:

- O tipo de aplicativo que você está compilando, como:
  - Aplicativo ( *. exe*) ou biblioteca ( *. dll*)
  - Aplicativo de navegador de Extensible Application Markup Language (XAML) (XBAP)
  - Aplicativo XAML flexível
  - Aplicativos instalados autônomos
  - Aplicativos autônomos implantados por ClickOnce
- A ferramenta de desenvolvimento, como:
  - MSBuild
  - Designer de gráfico de expressão
  - Designer interativo de expressão
  - Visual Studio
- A configuração da solução, como:
  - Uma solução
  - Um único projeto
  - Uma solução com vários projetos dependentes
- Se seu aplicativo tem recursos específicos a um idioma ou com neutralidade de idioma. Por exemplo, você especificou a propriedade do projeto `UICulture` ou os metadados localizáveis para os tipos `Application`, `Page`, e `Resource`?
- Se você usou a configuração de neutralidade de idioma no arquivo AssemblyInfo.cs ou AssemblyInfo.vb.

#### <a name="provide-scenario-and-impact-information"></a>Fornecer informações de cenário e impacto

Forneça informações sobre o cenário que manifesta o bug e seu impacto. Essas informações são altamente importantes para a equipe do WPF quando decidir se, quando e como um problema deve ser corrigido ou se uma solução alternativa aceitável pode ser usada em vez disso.

Normalmente, os cenários de perda de dados e de falhas são de alto impacto e, portanto, os mais fáceis de priorizar. Alguns bugs, no entanto, só aparecem em situações incomuns, que também podem ser cenários principais em alguns casos. Fornecer contexto em relação ao cenário e ao impacto ajuda a equipe do WPF a tomar a decisão certa.

## <a name="see-also"></a>Consulte também

- [Como relatar um problema com o Visual Studio](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)
