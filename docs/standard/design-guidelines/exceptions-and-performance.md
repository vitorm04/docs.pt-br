---
title: Exceções e desempenho
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
author: KrzysztofCwalina
ms.openlocfilehash: ab125117836545b9a2436347375ed0e08c591c7b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153742"
---
# <a name="exceptions-and-performance"></a>Exceções e desempenho
Uma preocupação comuns relacionada às exceções é que, se as exceções são usadas para o código que rotineiramente falha, o desempenho da implementação será inaceitável. Isso é uma preocupação válida. Quando um membro lança uma exceção, seu desempenho pode ser ordens de magnitude mais lentas. No entanto, é possível atingir um bom desempenho enquanto estritamente aderindo às diretrizes exceção que não é permitido usar códigos de erro. Dois padrões descritos nesta seção sugerem maneiras de fazer isso.  
  
 **X DO NOT** usar códigos de erro devido a questões que exceções podem afetar negativamente o desempenho.  
  
 Para melhorar o desempenho, é possível usar o padrão de testador mal-intencionado ou o padrão Try Parse, descritas nas próximas duas seções.  
  
## <a name="tester-doer-pattern"></a>Padrão de testador mal-intencionado  
 Às vezes, o desempenho de um membro de exceções pode ser melhorado ao dividir o membro em duas. Vamos examinar a <xref:System.Collections.Generic.ICollection%601.Add%2A> método da <xref:System.Collections.Generic.ICollection%601> interface.  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 O método `Add` gera se a coleção é somente leitura. Isso pode ser um problema de desempenho em cenários em que a chamada de método deve falhar com frequência. Uma das maneiras de atenuar o problema é se a coleção é gravável antes de tentar adicionar um valor de teste.  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 O membro usado para testar uma condição, que, em nosso exemplo, é a propriedade `IsReadOnly`, é conhecido como o testador. O membro usado para executar uma operação potencialmente gerando, o `Add` método em nosso exemplo, é conhecido como o mal-intencionado.  
  
 **✓ CONSIDER** o padrão de mal-intencionado Testador de membros que podem lançar exceções em comum em cenários para evitar problemas de desempenho relacionados a exceções.  
  
## <a name="try-parse-pattern"></a>Padrão de try Parse  
 Para APIs extremamente sensíveis ao desempenho, um padrão ainda mais rápido que o padrão de testador mal-intencionado descrito na seção anterior deve ser usado. O padrão de chamadas para ajustar o nome do membro para fazer um teste bem definido caso uma parte da semântica de membros. Por exemplo, <xref:System.DateTime> define um <xref:System.DateTime.Parse%2A> método que lança uma exceção se uma cadeia de caracteres de análise falhar. Ele também define uma correspondente <xref:System.DateTime.TryParse%2A> método que tenta analisar, mas retorna false se a análise for bem-sucedida e retorna o resultado de uma bem-sucedida análise usando um `out` parâmetro.  
  
```  
public struct DateTime {  
    public static DateTime Parse(string dateTime){   
        ...   
    }  
    public static bool TryParse(string dateTime, out DateTime result){  
        ...  
    }  
}  
```  
  
 Ao usar esse padrão, é importante definir a funcionalidade de try em termos estritos. Se o membro falhar por algum motivo que não seja a tentativa bem definido, o membro ainda deve lançar uma exceção correspondente.  
  
 **✓ CONSIDER** o padrão de Try-análise para os membros que podem lançar exceções em comum em cenários para evitar problemas de desempenho relacionados a exceções.  
  
 **✓ DO** usam o prefixo "Try" e Boolean tipo de retorno para métodos de implementar esse padrão.  
  
 **✓ DO** fornecem um membro geradoras de exceções para cada membro usando o padrão de análise de Try.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpresso com permissão da Pearson Education, Inc. de [as diretrizes de Design do Framework: As convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008 pela Addison-Wesley Professional, como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também

- [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
- [Diretrizes de design para exceções](../../../docs/standard/design-guidelines/exceptions.md)
