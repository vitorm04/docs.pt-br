---
title: Selar
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- limiting extensibility
- classes [.NET Framework], sealing
- preventing customization
- sealed classes
ms.assetid: cc42267f-bb7a-427a-845e-df97408528d4
ms.openlocfilehash: ddf463e98fb6a9c5ccaae90e9cfc74b5691b13a9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743616"
---
# <a name="sealing"></a>Selar
Um dos recursos das estruturas orientadas a objeto é que os desenvolvedores podem estendê-las e personalizá-las de maneiras inesperadas pelos designers de estrutura. Essa é a potência e o perigo do design extensível. Quando você projeta sua estrutura, é, portanto, muito importante projetar cuidadosamente a extensibilidade quando desejado e limitar a extensibilidade quando for perigoso.

 Um mecanismo poderoso que impede a extensibilidade esteja lacrando. Você pode lacrar a classe ou membros individuais. Lacrar uma classe impede que os usuários herdem da classe. Lacrar um membro impede que os usuários substituam um membro específico.

 ❌ não lacre as classes sem ter um bom motivo para fazer isso.

 Lacrar uma classe porque você não pode imaginar um cenário de extensibilidade não é um bom motivo. Os usuários do Framework gostam de herdar de classes por vários motivos não óbvios, como adicionar membros de conveniência. Veja [classes sem lacre](../../../docs/standard/design-guidelines/unsealed-classes.md) para obter exemplos de motivos não óbvios que os usuários desejam herdar de um tipo.

 Os bons motivos para lacrar uma classe incluem o seguinte:

- A classe é uma classe estática. Consulte [design de classe estática](../../../docs/standard/design-guidelines/static-class.md).

- A classe armazena segredos sensíveis à segurança em membros protegidos herdados.

- A classe herda muitos membros virtuais e o custo de lacre deles individualmente superaria os benefícios de deixar a classe sem lacre.

- A classe é um atributo que requer pesquisa de tempo de execução muito rápida. Os atributos lacrados têm níveis de desempenho ligeiramente mais altos do que os sem lacre. Consulte [atributos](../../../docs/standard/design-guidelines/attributes.md).

 ❌ não declare membros protegidos ou virtuais em tipos lacrados.

 Por definição, os tipos lacrados não podem ser herdados de. Isso significa que membros protegidos em tipos lacrados não podem ser chamados, e métodos virtuais em tipos lacrados não podem ser substituídos.

 ✔️ Considere lacrar os membros que você substitui.

 Problemas que podem resultar da introdução de membros virtuais (discutidos em [Membros virtuais](../../../docs/standard/design-guidelines/virtual-members.md)) também se aplicam a substituições, embora a um grau um pouco menor. Lacrar uma substituição protege você contra esses problemas começando do ponto na hierarquia de herança.

 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*

 *Reimpresso com permissão da Pearson Education, Inc. das [Diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicado em 22 de outubro de 2008 por Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*

## <a name="see-also"></a>Veja também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
- [Designer voltado para extensibilidade](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [Classes não seladas](../../../docs/standard/design-guidelines/unsealed-classes.md)
