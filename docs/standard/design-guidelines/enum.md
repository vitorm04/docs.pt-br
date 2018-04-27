---
title: Design de enum
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c3e89567761367ddcd67078b138c15b982a0d666
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="enum-design"></a>Design de enum
Enumerações são um tipo especial de tipo de valor. Há dois tipos de enums: enums enums e o sinalizador simples.  
  
 Enums simples representam pequenos conjuntos fechados de opções. Um exemplo comum de enum simple é um conjunto de cores.  
  
 Enumerações de sinalizador são projetadas para dar suporte a operações bit a bit com os valores de enum. Um exemplo comum de enum de sinalizadores é uma lista de opções.  
  
 **FAZER ✓** usar uma enumeração para fortemente tipados parâmetros, propriedades e retornam valores que representam os conjuntos de valores.  
  
 **FAZER ✓** favorecer usando um enum em vez de constantes estáticas.  
  
 **X não** usar uma enumeração para abrir conjuntos (como a versão do sistema operacional, os nomes dos seus amigos, etc.).  
  
 **X não** fornecer valores de enum reservado que se destinam para uso futuro.  
  
 Você sempre simplesmente pode adicionar valores para a enum existente em um estágio posterior. Consulte [adicionar valores para enumerações](#add_value) para obter mais detalhes sobre como adicionar valores para enums. Valores reservados apenas poluir o conjunto de valores reais e tendem a causar erros de usuário.  
  
 **X Evite** publicamente expondo enums com apenas um valor.  
  
 É uma prática comum para garantir a extensibilidade futura de APIs de C adicionar parâmetros reservados para assinaturas de método. Esses parâmetros reservados podem ser expressados como enums com um valor único padrão. Isso não deve ser feito de APIs gerenciadas. Sobrecarga de método permite a adição de parâmetros em versões futuras.  
  
 **X não** incluir valores de sentinela em enums.  
  
 Embora, às vezes, elas são úteis para os desenvolvedores do framework, os valores de sentinela são confusos para os usuários do framework. Eles são usados para controlar o estado de enum em vez de ser um dos valores do conjunto de representado por enum.  
  
 **FAZER ✓** fornecer um valor de zero em enumerações simples.  
  
 Considere a possibilidade de chamar o valor algo como "None". Se esse valor não é apropriado para essa enumeração específica, o valor padrão mais comum para a enum deve ser atribuído o valor subjacente do zero.  
  
 **✓ CONSIDERE** usando <xref:System.Int32> (o padrão na maioria das linguagens de programação) como o tipo subjacente de enum, a menos que qualquer um dos seguintes for verdadeiro:  
  
-   A enumeração é um enum de sinalizadores e você tem mais de 32 sinalizadores ou espera ter mais no futuro.  
  
-   O tipo subjacente deve ser diferente de <xref:System.Int32> mais fácil interoperabilidade com código não gerenciado esperando enums de tamanho diferente.  
  
-   Um tipo subjacente menores pode resultar em uma economia substancial no espaço. Se você espera que o enum a ser usada principalmente como um argumento para o fluxo de controle, o tamanho faz pouca diferença. A economia de tamanho pode ser significativa se:  
  
    -   Você espera que o enum a ser usado como um campo em uma classe ou estrutura instanciada com muita frequência.  
  
    -   Você espera que os usuários criem matrizes grandes ou coleções de enumerar instâncias.  
  
    -   Você espera que um grande número de instâncias do enum a ser serializado.  
  
 Para uso na memória, esteja ciente de que os objetos gerenciados são sempre `DWORD`-alinhado, portanto, você precisa efetivamente várias enums ou outras estruturas pequenas em uma instância para um enum menor do pacote para fazer a diferença, porque o tamanho de instância total é sempre vai ser arredondado para cima até um `DWORD`.  
  
 **FAZER ✓** nome do sinalizador enums com substantivos plurais ou frases nominais e simples enums com substantivos singulares ou frases nominais.  
  
 **X não** estender <xref:System.Enum?displayProperty=nameWithType> diretamente.  
  
 <xref:System.Enum?displayProperty=nameWithType> é um tipo especial usado pelo CLR para criar enumerações definidas pelo usuário. A maioria das linguagens de programação fornecem um elemento de programação que fornece acesso a essa funcionalidade. Por exemplo, no c# o `enum` palavra-chave é usada para definir uma enumeração.  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a>Projetando Enums de sinalizador  
 **FAZER ✓** se aplicam a <xref:System.FlagsAttribute?displayProperty=nameWithType> para enums de sinalizador. Não aplica esse atributo para enums simples.  
  
 **FAZER ✓** usar potências de dois para os valores de enumeração de sinalizador, portanto, eles podem ser livremente combinados usando a operação OR bit a bit.  
  
 **✓ CONSIDERE** fornecer valores de enum especial para comumente usadas combinações de sinalizadores.  
  
 Operações bit a bit são um conceito avançado e não será necessárias para tarefas simples. <xref:System.IO.FileAccess.ReadWrite> é um exemplo de tal um valor especial.  
  
 **X Evite** criando enums sinalizador onde algumas combinações de valores são inválidas.  
  
 **X Evite** usando o sinalizador valores de enumeração de zero, a menos que o valor representa a "todos os sinalizadores são desmarcados" e é denominado adequadamente, conforme descrito pela seguinte diretriz.  
  
 **FAZER ✓** o nome do valor zero de sinalizador enums `None`. Para um enum de sinalizador, o valor sempre deve significa "todos os sinalizadores são desmarcados."  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a>Adicionando o valor para Enums  
 É muito comum para descobrir o que você precisa adicionar valores a um enum depois que você já o tenha enviado. Há um possível problema de compatibilidade do aplicativo quando o valor recém-adicionado é retornado de uma API existente, como aplicativos mal escritos não podem tratar o novo valor corretamente.  
  
 **✓ CONSIDERE** adicionando valores a enums, apesar de um risco de compatibilidade pequeno.  
  
 Se você tiver dados reais sobre incompatibilidades entre aplicativos causados por adições para um enum, considere adicionar uma nova API que retorna os valores novos e antigos e substituir a antiga API, o que deve continuar a retornar apenas os valores antigos. Isso irá garantir que seus aplicativos existentes permanecem compatíveis.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de Design de tipo](../../../docs/standard/design-guidelines/type.md)  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)
