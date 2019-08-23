---
title: Resumo do tipo de dados (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Boolean data type [Visual Basic], supported types in Visual Basic
- storage [Visual Basic], order of storage
- data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], supported types in Visual Basic
- notation [Visual Basic], scientific
- memory requirements, data types
- user-defined data types [Visual Basic], Visual Basic
- Date data type [Visual Basic], Visual Basic
- Visual Basic, data types
- storage [Visual Basic], allocation
- Integer data type [Visual Basic], Visual Basic data types
- storage [Visual Basic], space
- Variant data types [Visual Basic], supported types in Visual Basic
- Char data type [Visual Basic], Visual Basic data types
- intrinsic data types [Visual Basic]
- memory consumption [Visual Basic], data types
- single-precision numbers
- data types [Visual Basic], order of storage
- Long data type [Visual Basic], supported types in Visual Basic
- String data type [Visual Basic], Visual Basic data types
- storage order, data types
- StructLayoutAttribute class, Visual Basic data type storage
- scientific notation
- Double data type [Visual Basic], Visual Basic data types
- Byte data type [Visual Basic], Visual Basic data types
- Object data type [Visual Basic], supported types in Visual Basic
- data types [Visual Basic], storage allocation
- double-precision numbers
- data types [Visual Basic], summary
- dates [Visual Basic], data types
- strings [Visual Basic], data types
- memory consumption
- storage order, controlling in Visual Basic
- data types [Visual Basic], memory requirements
ms.assetid: e975cdb6-64d8-4a4a-ae27-f3b3ed198ae0
ms.openlocfilehash: 57f6caa00806f4874cb8070805e8b6784ec82e40
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956797"
---
# <a name="data-type-summary-visual-basic"></a>Resumo do tipo de dados (Visual Basic)
A tabela a seguir mostra os tipos de dados Visual Basic, seus tipos de Common Language Runtime de suporte, sua alocação de armazenamento nominal e seus intervalos de valor.  
  
|Tipo de Visual Basic|Estrutura do tipo Common Language Runtime|Alocação de armazenamento nominal|Intervalo de valores|  
|-----------------------|--------------------------------------------|--------------------------------|-----------------|  
|[Booliano](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<xref:System.Boolean>|Depende da implementação da plataforma|`True` ou `False`|  
|[Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte>|1 byte|0 a 255 (não assinado)|  
|[Caractere](../../../visual-basic/language-reference/data-types/char-data-type.md) (caractere único)|<xref:System.Char>|2 bytes|0 a 65535 (não assinado)|  
|[Data](../../../visual-basic/language-reference/data-types/date-data-type.md)|<xref:System.DateTime>|8 bytes|0:00:00 (meia-noite) em 1º de janeiro de 0001 a 11:59:59 PM em 31 de dezembro de 9999|  
|[Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<xref:System.Decimal>|16 bytes|0 a +/-79228162514264337593543950335 (+/-7.9...E + 28) <sup>†</sup> sem ponto decimal; 0 a +/-7.9228162514264337593543950335 com 28 casas à direita do decimal;<br /><br /> o menor número diferente de zero é +/-0, 1 (+/-1E-28) <sup>†</sup>|  
|[Duplo](../../../visual-basic/language-reference/data-types/double-data-type.md) (ponto flutuante de precisão dupla)|<xref:System.Double>|8 bytes|-1.79769313486231570 e + 308 a-4.94065645841246544 E-324 <sup>†</sup> para valores negativos;<br /><br /> 4.94065645841246544 e-324 a 1.79769313486231570 E + 308 <sup>†</sup> para valores positivos|  
|[Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32>|4 bytes|-2.147.483.648 a 2.147.483.647 (assinado)|  
|[Longo](../../../visual-basic/language-reference/data-types/long-data-type.md) (inteiro longo)|<xref:System.Int64>|8 bytes|-9.223.372.036.854.775.808 a 9.223.372.036.854.775.807 (9.2... E + 18 <sup>†</sup>) (assinado)|  
|[Object](../../../visual-basic/language-reference/data-types/object-data-type.md)|<xref:System.Object>classes|4 bytes na plataforma de 32 bits<br /><br /> 8 bytes na plataforma de 64 bits|Qualquer tipo pode ser armazenado em uma variável do tipo`Object`|  
|[SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte>|1 byte|-128 a 127 (assinado)|  
|[Curto](../../../visual-basic/language-reference/data-types/short-data-type.md) (inteiro curto)|<xref:System.Int16>|2 bytes|-32.768 a 32.767 (assinado)|  
|[Único](../../../visual-basic/language-reference/data-types/single-data-type.md) (ponto flutuante de precisão simples)|<xref:System.Single>|4 bytes|-3.4028235 e + 38 a-1.401298 E-45 <sup>†</sup> para valores negativos;<br /><br /> 1.401298 e-45 a 3.4028235 E + 38 <sup>†</sup> para valores positivos|  
|[Cadeia de caracteres](../../../visual-basic/language-reference/data-types/string-data-type.md) (comprimento variável)|<xref:System.String>classes|Depende da implementação da plataforma|0 a aproximadamente 2.000.000.000 caracteres Unicode|  
|[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32>|4 bytes|0 a 4.294.967.295 (não assinado)|  
|[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64>|8 bytes|0 a 18446744073709551615 (1.8... E + 19 <sup>†</sup>) (não assinado)|  
|[Definido pelo usuário](../../../visual-basic/language-reference/data-types/user-defined-data-type.md) estruturá|(herda de <xref:System.ValueType>)|Depende da implementação da plataforma|Cada membro da estrutura tem um intervalo determinado por seu tipo de dados e independente dos intervalos dos outros membros|  
|[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16>|2 bytes|0 a 65.535 (não assinado)|  
  
 <sup>†</sup> Em *notação científica*, "E" refere-se a uma potência de 10. Portanto, 3.56 E + 2 significa 3,56 x 10<sup>2</sup> ou 356 E 3.56 e-2 significa 3,56/10<sup>2</sup> ou 0, 356.  
  
> [!NOTE]
> Para cadeias de caracteres que contêm <xref:Microsoft.VisualBasic.Strings.StrConv%2A> texto, use a função para converter de um formato de texto para outro.  
  
 Além de especificar um tipo de dados em uma instrução de declaração, você pode forçar o tipo de dados de alguns elementos de programação usando um caractere de tipo. Consulte [caracteres de tipo](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="memory-consumption"></a>Consumo de memória  
 Quando você declara um tipo de dados elementar, não é seguro supor que seu consumo de memória é o mesmo que sua alocação de armazenamento nominal. Isso se deve às seguintes considerações:  
  
- **Atribuição de armazenamento.** O Common Language Runtime pode atribuir armazenamento com base nas características atuais da plataforma na qual seu aplicativo está sendo executado. Se a memória estiver quase cheia, ela poderá empacotar seus elementos declarados o mais próximo possível. Em outros casos, ele pode alinhar seus endereços de memória a limites de hardware naturais para otimizar o desempenho.  
  
- **Largura da plataforma.** A atribuição de armazenamento em uma plataforma de 64 bits é diferente da atribuição em uma plataforma de 32 bits.  
  
### <a name="composite-data-types"></a>Tipos de dados compostos  
 As mesmas considerações se aplicam a cada membro de um tipo de dados composto, como uma estrutura ou uma matriz. Você não pode depender simplesmente de adicionar as alocações de armazenamento nominal dos membros do tipo. Além disso, há outras considerações, como as seguintes:  
  
- **Custos.** Alguns tipos compostos têm requisitos de memória adicionais. Por exemplo, uma matriz usa memória extra para a própria matriz e também para cada dimensão. Em uma plataforma de 32 bits, essa sobrecarga é, no momento, 12 bytes, mais 8 bytes para cada dimensão. Em uma plataforma de 64 bits, esse requisito é duplicado.  
  
- **Layout de armazenamento.** Você não pode supor com segurança que a ordem de armazenamento na memória é a mesma que a sua ordem de declaração. Você não pode até fazer suposições sobre o alinhamento de bytes, como um limite de 2 ou 4 bytes. Se você estiver definindo uma classe ou estrutura e precisar controlar o layout de armazenamento de seus membros, poderá aplicar o <xref:System.Runtime.InteropServices.StructLayoutAttribute> atributo à classe ou estrutura.  
  
### <a name="object-overhead"></a>Sobrecarga do objeto  
 Uma `Object` referência a qualquer tipo de dados elementar ou compostos usa 4 bytes além dos dados contidos no tipo de dados.  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Strings.StrConv%2A>
- <xref:System.Runtime.InteropServices.StructLayoutAttribute>
- [Funções de Conversão do Tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Resumo da Conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Caracteres de Tipo](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
- [Uso Eficiente de Tipos de Dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
