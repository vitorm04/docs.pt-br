---
title: Comentários da comunidade do WPF
ms.date: 03/01/2018
helpviewer_keywords:
- community resources [WPF]
- forums [WPF]
- bug descriptions [WPF]
ms.assetid: 468b060a-d54b-4900-a74a-9faccb554045
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f77058ac0cb87d0316395bce1dfb11401a2ce806
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921778"
---
# <a name="wpf-community-feedback"></a>Comentários da comunidade do WPF

A Microsoft expõe uma variedade de recursos da comunidade para que você conheça, discuta e forneça comentários sobre o Windows Presentation Foundation (WPF). Esses recursos incluem fóruns e o [comunidade de desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/) site. Cada recurso da comunidade oferece um conjunto diferente de benefícios. Esses benefícios são descritos aqui, como um conjunto de práticas recomendadas para serem usadas para garantir a melhor resposta da comunidade em geral e da Microsoft em particular.

> [!NOTE]
> Não use a seção de comentários localizada na parte inferior de cada página para enviar comentários sobre o produto. Esses links são apenas para comentários sobre a documentação.

## <a name="forums"></a>Fóruns

O [Fórum do WPF](https://social.msdn.microsoft.com/Forums/vstudio/en-US/home?forum=wpf) é um recurso principal da comunidade para discussão e resolução de problemas. Os fóruns facilitam a discussão e a resolução de problemas, oferecendo um conjunto abrangente de recursos de suporte que incluem:

- Pesquisa.
- Acompanhamento de discussão.
- Formatação avançada de texto e código.
- Integração com o Visual Studio.
- Envolvimento da comunidade e MVP (Most Valued Professional).
- Monitoramento para assegurar que as postagens sejam respondidas o mais rápido possível.

Outra opção para você fazer perguntas à comunidade sobre o WPF é [Stack Overflow](https://stackoverflow.com/questions/tagged/wpf).

### <a name="forum-best-practices"></a>Melhores práticas do Fórum

Usando as seguintes melhores práticas ajudam a resolver os problemas postados no Fórum do WPF no tempo mais rápido possível. Estas práticas são aplicáveis a todos os fóruns.

#### <a name="search-existing-posts"></a>Pesquisar postagens existentes

Alguns problemas ocorrem com tanta frequência que outros já os enfrentaram antes de você. Consequentemente, você pode resolver o problema rapidamente ou pode adicionar suas informações em uma discussão existente.

#### <a name="use-meaningful-titles"></a>Use títulos significativos

Títulos concisos e significativos melhoram a descoberta da sua postagem. Elas também tornam mais fácil para outros membros do fórum WPF determinar se eles podem solucionar seu problema.

#### <a name="include-appropriate-content"></a>Incluir conteúdo apropriado

Descreva o problema e como tentou resolvê-lo. Se possível, inclua snippets de código de suporte ou o exemplo mais simples possível que demonstre o seu problema. Todos esses detalhes ajudam a aumentar a chance de que sua pergunta seja respondida rapidamente.

## <a name="visual-studio-developer-community"></a>Comunidade de Desenvolvedores do Visual Studio

Às vezes, os problemas podem ser difíceis de resolver ou podem ser insolúveis. Essas situações ocorrem devido a bugs na tecnologia, dificuldades em aplicar a tecnologia a cenários específicos ou à falta de suporte para cenários específicos. Essa informação é importante para a Microsoft e pode ser fornecida por meio de [comunidade de desenvolvedores do Visual Studio](https://developercommunity.visualstudio.com/) site.

Itens postados no Centro de comentários de produto do WPF são roteadas para o banco de dados de bugs interno da equipe do WPF. Consequentemente, é a maneira mais confiável de receber seus comentários para o proprietário do recurso WPF. Além disso, você pode validar e acompanhar sugestões e bugs, bem como votar neles, que ajuda a equipe do WPF para priorizar problemas.

### <a name="developer-community-best-practices"></a>Práticas recomendadas de comunidade do desenvolvedor

No lançamento para a comunidade de desenvolvedores do Visual Studio, pesquisar envios existente, fornecer um título significativo e conteúdo apropriado são melhores práticas importantes, assim como são para a postagem no Fórum do WPF. Abaixo estão melhores práticas adicionais que você também deve empregar.

#### <a name="search-existing-posts"></a>Pesquisar postagens existentes

Alguns problemas ocorrem com tanta frequência que outros já os enfrentaram antes de você. Consequentemente, você pode resolver o problema rapidamente ou você pode adicionar sua entrada para um problema existente.

#### <a name="use-meaningful-titles"></a>Use títulos significativos

Títulos concisos e significativos aumentam as chances de que o problema seja direcionado para a equipe mais apropriada do WPF na menor quantidade de tempo. Isso é particularmente importante para uma tecnologia como WPF, que contém muitos recursos inter-relacionados.

#### <a name="describe-how-to-reproduce-your-bug"></a>Descreva como reproduzir o bug

Quando você posta a respeito de um bug, é importante incluir o seguinte nos locais relevantes:

- Forneça uma descrição clara do bug.
- Use snippets de código para dar suporte à descrição do bug.
- Forneça uma lista de etapas que demonstram como reproduzir o bug.
- Inclua o menor exemplo de código possível que reproduza o bug.
- Mencione se o bug é consistentemente reproduzível ou não.
- Inclua informações de exceção relevantes.

 Se o bug for relacionado à instalação ou à configuração, anexe os logs e instantâneos de instalação relevantes (arquivos prefixados com "dd _" que estão localizados na sua pasta %temp%).

 Para problemas relacionados ao build ou a compilação, anexe os logs de build. O sistema pode ser configurado do MSBuild dá suporte a registro em log com vários detalhamentos, usando a opção /v: na linha de comando ou configurando o nível apropriado de ambiente um desenvolvimento integrado (IDE) como o Visual Studio.

#### <a name="provide-environment-information"></a>Forneça informações de ambiente

Informações básicas geralmente podem ser úteis para adicionar contexto à sua postagem. Em particular, mencione a plataforma do sistema operacional, a família de processadores e a arquitetura, como "Windows 10 versão 1709, Intel (r) Xeon (r), x64".

Se o problema sobre o qual você está postando está relacionado à renderização, inclua também detalhes da placa e do driver de elementos gráficos, se possível. Essa informação é importante porque o WPF é uma estrutura de apresentação.

#### <a name="provide-solution-or-project-information"></a>Fornecer informações de solução ou projeto

Os bugs podem pertencer às ferramentas usadas para desenvolver e compilar seus aplicativos e aos tipos de aplicativos que você está compilando. Consequentemente, pode ser útil especificar:

- O tipo de aplicativo que você está compilando, como:
  - Aplicativo (*.exe*) ou biblioteca (*. dll*)
  - Aplicativo de navegador Extensible Application Markup Language (XAML) (XBAP)
  - Aplicativo de XAML flexível
  - Aplicativos autônomos instalado
  - Aplicativos autônomos implantados pelo ClickOnce
- A ferramenta de desenvolvimento, como:
  - MSBuild
  - Expression Graphic Designer
  - Expression Interactive Designer
  - Visual Studio
- A configuração da solução, como:
  - Uma solução
  - Um único projeto
  - Uma solução com vários projetos dependentes
- Se seu aplicativo tem recursos específicos a um idioma ou com neutralidade de idioma. Por exemplo, você especificou a propriedade do projeto `UICulture` ou os metadados localizáveis para os tipos `Application`, `Page`, e `Resource`?
- Se você usou a configuração de neutralidade de idioma no arquivo AssemblyInfo.cs ou AssemblyInfo.vb.

#### <a name="provide-scenario-and-impact-information"></a>Fornecer informações de cenário e de impacto

Fornecem informações sobre o cenário que manifesta o bug e seu impacto. Essas informações são altamente importantes para a equipe do WPF quando ele decide se, quando e como um problema deve ser corrigido, ou se uma solução alternativa aceitável pode ser usada em vez disso.

Normalmente, os cenários de perda de dados e de falhas são de alto impacto e, portanto, os mais fáceis de priorizar. Alguns bugs, no entanto, só aparecem em situações incomuns, que também podem ser cenários principais em alguns casos. Fornecer contexto ao redor do cenário e impacto ajuda a equipe do WPF a tomar a decisão certa.

## <a name="see-also"></a>Consulte também

- [Como relatar um problema com o Visual Studio 2017](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)
