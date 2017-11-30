---
title: "Desempenho e exceções"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9c2d7cfcb228c492d2adbe614d0ed88a3b02bb68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="exceptions-and-performance"></a>Desempenho e exceções
Uma preocupação comuns relacionada às exceções é que, se as exceções são usadas para código rotineiramente falha, o desempenho da implementação será inaceitável. Isso é uma preocupação válida. Quando um membro lança uma exceção, o desempenho pode ser mais lentas ordens de magnitude. No entanto, é possível atingir um bom desempenho ao estritamente aderindo às diretrizes de exceção que não é permitido usar códigos de erro. Dois padrões descritos nesta seção sugerem maneiras de fazer isso.  
  
 **X não** usar códigos de erro devido a questões que exceções podem afetar negativamente o desempenho.  
  
 Para melhorar o desempenho, é possível usar o testador mal-intencionado padrão ou o padrão de análise Try, descrito nas próximas duas seções.  
  
## <a name="tester-doer-pattern"></a>Testador mal-intencionado padrão  
 Às vezes, é possível melhorar o desempenho de um membro geradoras de exceções dividindo o membro em duas. Vamos examinar a <xref:System.Collections.Generic.ICollection%601.Add%2A> método o <xref:System.Collections.Generic.ICollection%601> interface.  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 O método `Add` lança a coleção é somente leitura. Isso pode ser um problema de desempenho em cenários em que a chamada do método deve falhar com frequência. Uma das maneiras de reduzir o problema é se a coleção é gravável antes de tentar adicionar um valor de teste.  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 O membro usado para testar uma condição, que, em nosso exemplo, é a propriedade `IsReadOnly`, é conhecido como o teste. O membro usado para executar uma operação potencialmente sendo lançada, o `Add` método em nosso exemplo, é conhecido como o mal-intencionado.  
  
 **✓ CONSIDERE** o padrão de mal-intencionado Testador de membros que podem lançar exceções em comum em cenários para evitar problemas de desempenho relacionados a exceções.  
  
## <a name="try-parse-pattern"></a>Tente a análise padrão  
 Para desempenho extremamente sensíveis APIs, um padrão ainda mais rápido do que o padrão de testador mal-intencionado descrito na seção anterior deve ser usado. O padrão de chamadas para ajustar o nome do membro para fazer um teste bem definido caso uma parte da semântica de membros. Por exemplo, <xref:System.DateTime> define um <xref:System.DateTime.Parse%2A> método que gera uma exceção se a análise de uma cadeia de caracteres falhar. Ele também define correspondente <xref:System.DateTime.TryParse%2A> método que tenta analisar, mas retornará false se a análise for bem-sucedida e retorna o resultado de uma análise com êxito usando um `out` parâmetro.  
  
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
  
 Ao usar esse padrão, é importante definir a funcionalidade de tente em termos estritos. Se o membro falhar por algum motivo que não seja o tente bem definido, o membro ainda deve lançar uma exceção correspondente.  
  
 **✓ CONSIDERE** o padrão de Try-análise para os membros que podem lançar exceções em comum em cenários para evitar problemas de desempenho relacionados a exceções.  
  
 **FAZER ✓** usam o prefixo "Try" e Boolean tipo de retorno para métodos de implementar esse padrão.  
  
 **FAZER ✓** fornecem um membro geradoras de exceções para cada membro usando o padrão de análise de Try.  
  
 *Partes © 2005, 2009 Microsoft Corporation. Todos os direitos reservados.*  
  
 *Reimpressas pela permissão de Pearson educação, Inc. de [diretrizes de Design do Framework: convenções, linguagens e padrões para bibliotecas do .NET reutilizável, 2ª edição](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) por Krzysztof Cwalina e Brad Abrams, publicados 22 de outubro de 2008, Addison-Wesley Professional como parte da série de desenvolvimento do Microsoft Windows.*  
  
## <a name="see-also"></a>Consulte também  
 [Diretrizes de design do Framework](../../../docs/standard/design-guidelines/index.md)  
 [Diretrizes de design para exceções](../../../docs/standard/design-guidelines/exceptions.md)
