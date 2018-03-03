---
title: "Comentários da comunidade WPF"
ms.date: 03/01/2018
ms.prod: .net-framework
ms.technology:
- dotnet-wpf
ms.topic: article
helpviewer_keywords:
- community resources [WPF]
- forums [WPF]
- bug descriptions [WPF]
ms.assetid: 468b060a-d54b-4900-a74a-9faccb554045
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 243e40b1b16fd88a786398c15cd29a5baeacd6ac
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2018
---
# <a name="wpf-community-feedback"></a>Comentários da comunidade WPF

A Microsoft expõe uma variedade de recursos da comunidade para que você conheça, discuta e fornecer comentários sobre o Windows Presentation Foundation (WPF). Esses recursos incluem fóruns e [comunidade de desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/) site. Cada recurso da comunidade oferece um conjunto diferente de benefícios. Esses benefícios são descritos aqui, como um conjunto de práticas recomendadas para usar cada um para garantir a melhor resposta da comunidade e Microsoft em particular.

> [!NOTE]
> Não use a seção de comentários localizada na parte inferior de cada página para enviar comentários sobre o produto. Esses links são apenas para comentários sobre a documentação.

## <a name="forums"></a>Fóruns

O [Fórum do WPF](https://social.msdn.microsoft.com/Forums/vstudio/en-US/home?forum=wpf) é o recurso principal da comunidade para discutir e solucionar problemas. Os fóruns facilitam a discussão e a resolução de problemas, oferecendo um conjunto abrangente de recursos de suporte que incluem:

- Pesquisa.
- Acompanhamento de discussão.
- Formatação avançada de texto e código.
- Integração do Visual Studio.
- Envolvimento da comunidade e MVP (Most Valued Professional).
- Monitoramento para assegurar que as postagens sejam respondidas o mais rápido possível.

Outra opção para que você faça perguntas para a comunidade sobre o WPF é [estouro de pilha](https://stackoverflow.com/questions/tagged/wpf).

### <a name="forum-best-practices"></a>Práticas recomendadas do Fórum

Usar o seguinte melhor práticas ajuda a resolver problemas postados no Fórum do WPF no tempo mais rápido possível. Estas práticas são aplicáveis a todos os fóruns.

#### <a name="search-existing-posts"></a>Pesquisar postagens existentes

Alguns problemas ocorrem com tanta frequência que outros já os enfrentaram antes de você. Consequentemente, você pode resolver o problema rapidamente ou pode adicionar suas informações em uma discussão existente.

#### <a name="use-meaningful-titles"></a>Usar títulos significativos

Títulos concisos e significativos melhoram o significado da sua postagem. Eles também o tornam mais fácil para outros membros da comunidade fórum WPF determinar se eles podem solucionar seu problema.

#### <a name="include-appropriate-content"></a>Incluir conteúdo apropriado

Descreva o problema e como você tentou trabalhar com ele. Se possível, inclua trechos de código de suporte ou o exemplo mais simples possível que demonstre o seu problema. Todos esses detalhes ajudam a aumentar a chance de que sua pergunta seja respondida rapidamente.

## <a name="visual-studio-developer-community"></a>Comunidade de desenvolvedores do Visual Studio

Às vezes, os problemas podem ser difíceis de resolver ou podem ser insolúveis. Essas situações ocorrem devido a bugs na tecnologia, dificuldades em aplicar a tecnologia a cenários específicos ou à falta de suporte para cenários específicos. Essa informação é importante para a Microsoft e pode ser fornecida por meio de [comunidade de desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/) site.

Itens postados no Centro de comentários do produto WPF são roteadas para o banco de dados de bugs internos da equipe do WPF. Consequentemente, é a maneira mais confiável para receber seus comentários para o proprietário do recurso WPF. Além disso, você pode validar e controlar sugestões e bugs, bem como votar neles, que ajuda a equipe do WPF para priorizar problemas.

### <a name="developer-community-best-practices"></a>Práticas recomendadas do desenvolvedor da comunidade

Ao lançar o Visual Studio Developer Community, pesquisar envios existente, fornecer um título significativo e conteúdo apropriado são importantes práticas recomendadas, como elas são de lançamento para o fórum do WPF. Abaixo estão melhores práticas adicionais que você também deve empregar.

#### <a name="search-existing-posts"></a>Pesquisar postagens existentes

Alguns problemas ocorrem com tanta frequência que outros já os enfrentaram antes de você. Consequentemente, você pode resolver o problema rapidamente, ou você pode adicionar a entrada para um problema existente.

#### <a name="use-meaningful-titles"></a>Usar títulos significativos

Títulos concisos e significativos aumentam a oportunidade de que o problema será direcionado para a equipe WPF mais apropriada na menor quantidade de tempo. Isso é particularmente importante para uma tecnologia como WPF, que contém muitos recursos inter-relacionados.

#### <a name="describe-how-to-reproduce-your-bug"></a>Descreve como reproduzir o erro

Quando você posta a respeito de um bug, é importante incluir o seguinte nos locais relevantes:

- Forneça uma descrição clara do bug.
- Use trechos de código para dar suporte à descrição do bug.
- Forneça uma lista de etapas que demonstram como reproduzir o bug.
- Inclua o menor exemplo de código possível que reproduza o bug.
- Mencione se o bug é consistentemente reproduzível ou não.
- Inclua informações de exceção relevantes.

 Se o bug for relacionado à instalação ou à configuração, anexe os logs e instantâneos de instalação relevantes (arquivos prefixados com "dd _" que estão localizados na sua pasta %temp%).

 Para problemas relacionados ao build ou a compilação, anexe os logs de build. O MSBuild sistema pode ser configurado para oferece suporte ao registro em log com vários verbosities usando a opção /v: na linha de comando ou configurando o nível apropriado de ambiente um desenvolvimento integrado (IDE) como o Visual Studio.

#### <a name="provide-environment-information"></a>Fornecer informações de ambiente

Informações básicas geralmente podem ser úteis para adicionar contexto à sua postagem. Em particular, mencione a plataforma de sistema operacional, a família de processadores e a arquitetura, como "Windows 10 versão 1709, Intel (r) Xeon (r), x64".

Se o problema sobre o qual você está postando está relacionado à renderização, inclua também detalhes da placa e do driver de elementos gráficos, se possível. Essa informação é importante porque o WPF é uma estrutura de apresentação.

#### <a name="provide-solution-or-project-information"></a>Fornecer informações de solução ou projeto

Os bugs podem pertencer às ferramentas usadas para desenvolver e compilar seus aplicativos e aos tipos de aplicativos que você está compilando. Consequentemente, pode ser útil especificar:

- O tipo de aplicativo que você está compilando, como:
  - Aplicativo (*.exe*) ou biblioteca (*. dll*)
  - Extensible Application Markup Language (XAML) navegador XBAP (aplicativo)
  - Aplicativo solto de XAML
  - Aplicativos autônomos instalados
  - Aplicativos ClickOnce implantados autônomo
- A ferramenta de desenvolvimento, como:
  - MSBuild
  - Designer gráfico de expressão
  - Expressão Interactive Designer
  - Visual Studio
- A configuração da solução, como:
  - Uma solução
  - Um único projeto
  - Uma solução com vários projetos dependentes
- Se seu aplicativo tem recursos específicos a um idioma ou com neutralidade de idioma. Por exemplo, você especificou a propriedade do projeto `UICulture` ou os metadados localizáveis para os tipos `Application`, `Page`, e `Resource`?
- Se você usou a configuração de neutralidade de idioma no arquivo AssemblyInfo.cs ou AssemblyInfo.vb.

#### <a name="provide-scenario-and-impact-information"></a>Fornecer informações de impacto e de cenário

Fornece informações sobre o cenário que manifesta o erro e seu impacto. Essas informações são altamente importantes para a equipe WPF quando ela decide se, quando e como um problema deve ser corrigido, ou se uma solução aceitável pode ser usada em vez disso.

Normalmente, os cenários de perda de dados e de falhas são de alto impacto e, portanto, os mais fáceis de priorizar. Alguns bugs, no entanto, só aparecem em situações incomuns, que também podem ser cenários principais em alguns casos. Fornecer contexto ao redor cenário e impacto ajuda a equipe WPF tomar a decisão certa.

## <a name="see-also"></a>Consulte também

[Como relatar um problema com o Visual Studio 2017](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)
