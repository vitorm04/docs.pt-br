---
title: Design de enumeração
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
author: KrzysztofCwalina
ms.openlocfilehash: c0645ba1179c4c6fd961b871b3061cd51174f427
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54675141"
---
# <a name="enum-design"></a>Design de enumeração
Enumerações são um tipo especial de tipo de valor. Há dois tipos de enums: enums de enums e sinalizador simples.  
  
 Enums simples representam conjuntos fechados pequeno de opções. Um exemplo comum de enum simple é um conjunto de cores.  
  
 Enums do sinalizador são projetados para dar suporte a operações bit a bit com os valores de enumeração. Um exemplo comum de enumeração de sinalizadores é uma lista de opções.  
  
 **✓ DO** usar uma enumeração para fortemente tipados parâmetros, propriedades e retornam valores que representam os conjuntos de valores.  
  
 **✓ DO** favorecer usando um enum em vez de constantes estáticas.  
  
 **X DO NOT** usar uma enumeração para abrir conjuntos (como a versão do sistema operacional, os nomes dos seus amigos, etc.).  
  
 **X DO NOT** fornecer valores de enum reservado que se destinam para uso futuro.  
  
 Você sempre simplesmente pode adicionar valores para o enum existente em um estágio posterior. Ver [adicionando valores a Enums](#add_value) para obter mais detalhes sobre como adicionar valores a enums. Valores reservados simplesmente poluam o conjunto de valores reais e tendem a levar a erros de usuário.  
  
 **X AVOID** publicamente expondo enums com apenas um valor.  
  
 É uma prática comum para garantir a futura extensibilidade das APIs de C adicionar parâmetros reservados a assinaturas de método. Esses parâmetros reservados podem ser expresso como enums com um valor padrão único. Isso não deve ser feito em APIs gerenciadas. Sobrecarga de método permite a adição de parâmetros em versões futuras.  
  
 **X DO NOT** incluir valores de sentinela em enums.  
  
 Embora, às vezes, eles são úteis para desenvolvedores do framework, os valores de sentinela são confusos para os usuários do framework. Eles são usados para controlar o estado de enumeração em vez de ser um dos valores do conjunto representado pela enumeração.  
  
 **✓ DO** fornecer um valor de zero em enumerações simples.  
  
 Considere a possibilidade de chamar o valor de algo como "None". Se esse valor não for apropriado para essa enum específica, o valor padrão mais comum para o enum deve ser atribuído o valor subjacente de zero.  
  
 **✓ CONSIDER** usando <xref:System.Int32> (o padrão na maioria das linguagens de programação) como o tipo subjacente de enum, a menos que qualquer um dos seguintes for verdadeiro:  
  
-   Enum é uma enumeração de sinalizadores e você tiver mais de 32 sinalizadores ou pretende ter mais no futuro.  
  
-   O tipo subjacente deve ser diferente de <xref:System.Int32> mais fáceis de interoperabilidade com código não gerenciado, esperando enums de tamanho diferente.  
  
-   Um tipo subjacente menor poderia resultar em uma economia substancial no espaço. Se você espera que o enum a ser usado principalmente como um argumento para o fluxo de controle, o tamanho torna pouca diferença. A economia de tamanho pode ser significativa se:  
  
    -   Você espera que o enum a ser usado como um campo em uma classe ou estrutura com muita frequência instanciada.  
  
    -   Você espera que os usuários criem matrizes grandes ou coleções de enumerar instâncias.  
  
    -   Você espera que um grande número de instâncias de enum deve ser serializada.  
  
 Para uso na memória, esteja ciente de que os objetos gerenciados são sempre `DWORD`-alinhados, portanto, você precisa efetivamente várias enumerações ou outras estruturas pequenas em uma instância para empacotar um enum menor com para fazer uma diferença, porque o tamanho total de instâncias é sempre vai ser arredondado para um `DWORD`.  
  
 **✓ DO** nome do sinalizador enums com substantivos plurais ou frases nominais e simples enums com substantivos singulares ou frases nominais.  
  
 **X DO NOT** estender <xref:System.Enum?displayProperty=nameWithType> diretamente.  
  
 <xref:System.Enum?displayProperty=nameWithType> é um tipo especial usado pelo CLR para criar enumerações definidas pelo usuário. A maioria das linguagens de programação fornece um elemento de programação que dá acesso a essa funcionalidade. Por exemplo, em c# a `enum` palavra-chave é usada para definir uma enumeração.  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a>Projetando Enums de sinalizador  
 **✓ DO** se aplicam a <xref:System.FlagsAttribute?displayProperty=nameWithType> para enums de sinalizador. Não aplique esse atributo para enums simples.  
  
 **✓ DO** usar potências de dois para os valores de enumeração de sinalizador, portanto, eles podem ser livremente combinados usando a operação OR bit a bit.  
  
 **✓ CONSIDER** fornecer valores de enum especial para comumente usadas combinações de sinalizadores.  
  
 Operações bit a bit são um conceito avançado e não devem ser necessárias para tarefas simples. <xref:System.IO.FileAccess.ReadWrite> é um exemplo de um valor especial.  
  
 **X AVOID** criando enums sinalizador onde algumas combinações de valores são inválidas.  
  
 **X AVOID** usando o sinalizador valores de enumeração de zero, a menos que o valor representa a "todos os sinalizadores são desmarcados" e é denominado adequadamente, conforme descrito pela seguinte diretriz.  
  
 **✓ DO** o nome do valor zero de sinalizador enums `None`. Para uma enumeração de sinalizador, o valor sempre deve significar "todos os sinalizadores são desmarcados."  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a>Adicionando o valor para Enums  
 É muito comum para descobrir o que você precisa adicionar valores a uma enum depois que você já tiver enviado ele. Há um problema potencial de compatibilidade do aplicativo quando o valor recém-adicionado é retornado de uma API existente, porque aplicativos mal escritos não podem manipular o novo valor corretamente.  
  
 **✓ CONSIDER** adicionando valores a enums, apesar de um risco de compatibilidade pequeno.  
  
 Se você tiver dados reais sobre incompatibilidades de aplicativos causados por adições a uma enum, considere adicionar uma nova API que retorna os valores novos e antigos e substituir a antiga API, o que deve continuar retornando apenas os valores antigos. Isso garantirá que seus aplicativos existentes permanecem compatíveis.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de Design de tipo](../../../docs/standard/design-guidelines/type.md)
- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
