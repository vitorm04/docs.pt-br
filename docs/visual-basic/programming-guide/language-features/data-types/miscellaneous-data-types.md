---
title: Tipos de dados diversos
ms.date: 07/20/2015
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
ms.openlocfilehash: cc6262b5bb305bb839917e222d831fa3340a1b14
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346344"
---
# <a name="miscellaneous-data-types-visual-basic"></a>Tipos de dados diversos (Visual Basic)
O Visual Basic fornece vários tipos de dados que não são orientados para números ou caracteres. Em vez disso, eles lidam com dados especializados, como valores Sim/Não, valores de data/hora e endereços de objeto.  
  
 Para uma tabela que mostra uma comparação lado a lado do Visual Basic tipos de dados, consulte [tipos de dados](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="boolean-type"></a>Tipo booliano  
 O [tipo de dados booliano](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) é um valor não assinado que é interpretado como `True` ou `False`. Sua largura de dados depende da plataforma de implementação. Se uma variável puder conter apenas valores de dois Estados, como true/false, yes/no ou on/off, declare-a como `Boolean`.  
  
## <a name="date-type"></a>Tipo de data  
 O [tipo de dados Date](../../../../visual-basic/language-reference/data-types/date-data-type.md) é um valor de 64 bits que contém as informações de data e hora. Cada incremento representa 100 nanossegundos de tempo decorrido desde o início (12:00 AM) de 1º de Janeiro do ano 1 no calendário gregoriano. Se uma variável puder conter um valor de data, um valor de hora ou ambos, declare-a como `Date`.  
  
## <a name="object-type"></a>{1&gt;{2&gt;Tipo de Objeto&lt;2}&lt;1}  
 O [tipo de dados Object](../../../../visual-basic/language-reference/data-types/object-data-type.md) é um endereço de 32 bits que aponta para uma instância de objeto dentro de seu aplicativo ou em algum outro aplicativo. Uma variável `Object` pode se referir a qualquer objeto que seu aplicativo reconhece ou a dados de qualquer tipo de dados. Isso inclui os dois *tipos de valor*, como `Integer`, `Boolean`e instâncias de estrutura, e tipos de *referência*, que são instâncias de objetos criados a partir de classes como `String` e <xref:System.Windows.Forms.Form>e instâncias de matriz.  
  
 Se uma variável armazena um ponteiro para uma instância de uma classe que você não conhece no momento da compilação, ou se ele pode apontar para dados de vários tipos de dados, declare-o como `Object`.  
  
 A vantagem do tipo de dados `Object` é que você pode usá-lo para armazenar dados de qualquer tipo de dados. A desvantagem é que você incorre em operações extras que levam mais tempo de execução e tornam seu aplicativo mais lento. Se você usar uma variável `Object` para tipos de valor, você incorrerá em *Boxing* e *unboxing*. Se você usá-lo para tipos de referência, você incorrerá em *associação tardia*.  
  
## <a name="see-also"></a>Consulte também

- [Caracteres de Tipo](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Tipos de Dados Elementares](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Tipos de Dados Numéricos](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [Tipos de Dados de Caractere](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)
- [Solução de problemas de Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Associação Antecipada e Tardia](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
