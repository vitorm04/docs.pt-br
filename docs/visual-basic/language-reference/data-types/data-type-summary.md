---
title: "Resumo do tipo de dados (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "tipo de dados Booliano, tipos com suporte no Visual Basic"
  - "tipo de dados Byte, tipos de dados do Visual Basic"
  - "tipo de dados Char, tipos de dados do Visual Basic"
  - "tipos de dados [Visual Basic], requisitos de memória"
  - "tipos de dados [Visual Basic], ordem de armazenamento"
  - "tipos de dados [Visual Basic], alocação de armazenamento"
  - "tipos de dados [Visual Basic], resumo"
  - "tipos de dados [Visual Basic], Visual Basic"
  - "tipo de dados de data, Visual Basic"
  - "datas [Visual Basic], tipos de dados"
  - "tipo de dados Double, tipos de dados do Visual Basic"
  - "números de precisão dupla"
  - "tipo de dados Integer, tipos de dados do Visual Basic"
  - "tipos de dados intrínsecos"
  - "tipo de dados Long, tipos com suporte no Visual Basic"
  - "consumo de memória"
  - "consumo de memória, tipos de dados"
  - "requisitos de memória, tipos de dados"
  - "notação, científica"
  - "tipo de dados Object, tipos com suporte no Visual Basic"
  - "notação científica"
  - "tipo de dados Single, tipos com suporte no Visual Basic"
  - "números de precisão única"
  - "ordem de armazenamento, controlando no Visual Basic"
  - "ordem de armazenamento, tipos de dados"
  - "armazenamento, alocação"
  - "armazenamento, ordem de armazenamento"
  - "armazenamento, espaço"
  - "tipo de dados String, tipos de dados do Visual Basic"
  - "cadeias de caracteres {Visual Basic], tipos de dados"
  - "Classe StructLayoutAttribute, armazenamento de tipo de dados do Visual Basic"
  - "tipos de dados definidos pelo usuário, Visual Basic"
  - "tipos de dados Variant, tipos com suporte no Visual Basic"
  - "Visual Basic, tipos de dados"
ms.assetid: e975cdb6-64d8-4a4a-ae27-f3b3ed198ae0
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Resumo do tipo de dados (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

A tabela seguinte mostra tipos de dado do Visual Basic, o tempo de execução de suporte language runtime digita, a alocação de armazenamento substantiva, e seus intervalos de valores.  
  
|Tipo do Visual Basic|Estrutura do tipo do common language runtime|Alocação de armazenamento substantiva|Intervalo valor|  
|--------------------------|--------------------------------------------------|-------------------------------------------|---------------------|  
|[Booleano](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<xref:System.Boolean>|Implementar depende da plataforma|`True` ou `False`|  
|[Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte>|1 bytes|0 a 255 \(sem sinal\)|  
|[Char](../../../visual-basic/language-reference/data-types/char-data-type.md) \(caractere único\)|<xref:System.Char>|2 bytes|0 a 65535 \(sem sinal\)|  
|[Date](../../../visual-basic/language-reference/data-types/date-data-type.md)|<xref:System.DateTime>|8 bytes|0:00: 00 \(meia\-noite\) o 1º de janeiro, 0001 com o 11:59: 59. O 31, 9999 de dezembro|  
|[Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<xref:System.Decimal>|16 bytes|0 através \+\/\-0.0000000000000000000000000001 \(\+\/\-7.9228162514264337593543950335 \-79.228.162.514.264.337.593.543.950.335 \-7,9… E\+28\) <sup>†</sup> sem o ponto decimal; 0 por meio para \+\/\- \-7,9228162514264337593543950335 com um de 28 locais para a direita do decimal;<br /><br /> o número diferente de zero o menor é \+\/\-7.9228162514264337593543950335 \-0,0000000000000000000000000001 \(\+\/\-1E\-28\) <sup>†</sup>|  
|\([Duplo](../../../visual-basic/language-reference/data-types/double-data-type.md) de ponto flutuante de precisão dupla\)|<xref:System.Double>|8 bytes|\-1.79769313486231570E\+308 até \-4.94065645841246544E\-324 <sup>†</sup> para valores negativos;<br /><br /> 4.94065645841246544E\-324 para 1.79769313486231570E\+308 <sup>†</sup> para valores positivos|  
|[Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32>|4 bytes|\-2.147.483.648 a 2.147.483.647 \(assinado\)|  
|[Long](../../../visual-basic/language-reference/data-types/long-data-type.md) inteiro longo \(\)|<xref:System.Int64>|8 bytes|\-9.223.372.036.854.775.808 a 9.223.372.036.854.775.807 \(9,2… E\+18 <sup>†</sup>\) \(assinados\)|  
|[Object](../../../visual-basic/language-reference/data-types/object-data-type.md)|<xref:System.Object> \(classe\)|4 bytes na plataforma de 32 bits<br /><br /> 8 bytes na plataforma de 64 bits|Qualquer tipo pode ser armazenado em uma variável do tipo `Object`|  
|[SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte>|1 bytes|\-128 a 127 \(assinado\)|  
|[Short](../../../visual-basic/language-reference/data-types/short-data-type.md) inteiro \(curto\)|<xref:System.Int16>|2 bytes|\-32.768 a 32.767 \(assinado\)|  
|\([Única](../../../visual-basic/language-reference/data-types/single-data-type.md) de ponto flutuante de precisão simples\)|<xref:System.Single>|4 bytes|até \-1.401298e <sup>†</sup> \- 3.4028235e\+38 para valores negativos;<br /><br /> variando para valores positivos a 3.4028235E\+38 <sup>†</sup>|  
|[Cadeia de caracteres](../../../visual-basic/language-reference/data-types/string-data-type.md) de comprimento variável\)|<xref:System.String> \(classe\)|Implementar depende da plataforma|aproximadamente 0 a 2 caracteres Unicode bilhão|  
|[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32>|4 bytes|0 a 4.294.967.295 \(sem sinal\)|  
|[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64>|8 bytes|0 a 18.446.744.073.709.551.615 \(1,8… E\+19 <sup>†</sup>\) \(sem sinal\)|  
|[Definido pelo usuário](../../../visual-basic/language-reference/data-types/user-defined-data-type.md) \(estrutura\)|\(herda de <xref:System.ValueType>\)|Implementar depende da plataforma|Cada membro de estrutura tem um intervalo determinado por seu tipo de dados e independente de intervalos de outros membros|  
|[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16>|2 bytes|0 a 65.535 \(sem sinal\)|  
  
 <sup>†</sup> *Na notação científica*, “E” refere\-se a uma potência de 10.  Portanto 3.56E\+2 significa 3,56 x 10<sup>2</sup> ou 356, e 3.56E\-2 significa 3,56 \/ 10<sup>2</sup> ou 0,0356.  
  
> [!NOTE]
>  Para cadeias de caracteres que contêm texto, use a função de <xref:Microsoft.VisualBasic.Strings.StrConv%2A> para converter de um formato de texto para outro.  
  
 Além de especificar um tipo de dados em uma instrução de declaração, você pode forçar o tipo de dados de alguns elementos de programação usando um caractere de tipo.  Consulte [Caracteres de tipo](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## Consumo de memória  
 Quando você declara um tipo de dados elementar, não é seguro suponha que seu consumo de memória é o mesmo que a alocação de armazenamento substantiva.  Isso é devido às seguintes condições:  
  
-   **Atribuição de armazenamento.** O common language runtime pode atribuir o armazenamento com base nas características atuais de plataforma no qual seu aplicativo está sendo executado.  Se a memória está quase completa, pode compactar os seus elementos declarados tão próximas uma possível.  Em outros casos pode alinhar os endereços de memória para os limites naturais de hardware para otimizar o desempenho.  
  
-   **Largura da plataforma.** A atribuição de armazenamento em uma plataforma de 64 bits é diferente de atribuir em uma plataforma de 32 bits.  
  
### Tipos de dados compostos  
 As mesmas considerações se aplicam a cada membro de um tipo de dados composto, como uma estrutura ou uma matriz.  Você não pode depender simplesmente adicionar juntos nas alocações de armazenamento nominais de membros do tipo.  Além disso, há outras considerações, como o seguinte:  
  
-   **Sobrecarga.** Alguns tipos compostos têm requisitos de memória adicionais.  Por exemplo, uma matriz usa a memória adicional para a própria matriz e também para cada dimensão.  Em uma plataforma de 32 bits, essa sobrecarga está atualmente 12 bytes mais 8 bytes para cada dimensão.  Em uma plataforma de 64 bits esse requisito é duplicado.  
  
-   **Layout do armazenamento.** Você não pode assumir com segurança que a ordem de armazenamento na memória é o mesmo que suas declarações.  Você pode nem fazer suposições sobre o alinhamento de bytes, como limite de 2 bytes um byte ou 4.  Se você estiver definindo uma classe ou estrutura e você precisam controlar o layout do armazenamento de seus membros, você pode aplicar o atributo de <xref:System.Runtime.InteropServices.StructLayoutAttribute> a classe ou estrutura.  
  
### Sobrecarga de objeto  
 `Object` fazendo referência a qualquer tipo de dados elementar ou composto usa 4 bytes além dos dados contidos no tipo de dados.  
  
## Consulte também  
 <xref:Microsoft.VisualBasic.Strings.StrConv%2A>   
 <xref:System.Runtime.InteropServices.StructLayoutAttribute>   
 [Funções de conversão do tipo](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Resumo da conversão](../../../visual-basic/language-reference/keywords/conversion-summary.md)   
 [Caracteres de tipo](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Uso eficiente de tipos de dados](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)