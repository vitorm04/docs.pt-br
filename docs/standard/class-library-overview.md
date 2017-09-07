---
title: "Visão geral da biblioteca de classes .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- classes [.NET Framework], library overview
- class objects value type
- naming conventions [.NET Framework]
- types, .NET Framework
- user-defined types
- Visual Basic, data types
- data types [.NET Framework], C++
- Visual C#, data types
- libraries, .NET Framework class library
- data types [.NET Framework], JScript
- System namespace
- JScript, data types
- .NET Framework, class library
- type system [.NET Framework]
- data types [.NET Framework]
- value types
- data types [.NET Framework], Visual Basic
- Common Language Specification
- namespaces [.NET Framework]
- floating point value type
- class library [.NET Framework]
- CLS
- logical value type
- .NET Framework class library, about
- built-in types
- namespaces [.NET Framework], about namespaces
- Visual C++, data types
- members [.NET Framework], type
- data types [.NET Framework], C#
- integer value type
- base types, class library
ms.assetid: 7e4c5921-955d-4b06-8709-101873acf157
caps.latest.revision: 19
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b88c85eaeabc7fa87b483c7302bd5e135e3fd276
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="net-framework-class-library-overview"></a>Visão geral da biblioteca de classes .NET Framework
O [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] inclui as classes, as interfaces e os tipos de valor que agilizam e otimizam o processo de desenvolvimento e dão acesso à funcionalidade do sistema. Para facilitar a interoperabilidade entre linguagens, os tipos do .NET Framework são compatíveis com CLS e, assim, podem ser usados por qualquer linguagem de programação cujo compilador esteja de acordo com a CLS (Common Language Specification).  
  
 Os tipos do .NET Framework formam a base na qual os aplicativos, os componentes e os controles do .NET são compilados. O [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] inclui tipos que executam as seguintes funções:  
  
-   Representam tipos de dados base e exceções.  
  
-   Encapsulam estruturas de dados.  
  
-   Executam E/S.  
  
-   Acessam informações sobre tipos carregados.  
  
-   Invocam verificações de segurança do .NET Framework.  
  
-   Fornecem acesso a dados, uma GUI detalhada do lado do cliente e uma GUI do lado do cliente controlada pelo servidor.  
  
 O [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] fornece um conjunto avançado de interfaces, bem como classes abstratas e concretas (não abstratas). Você pode usar as classes concretas como estão ou, em muitos casos, pode derivar suas próprias classes a partir delas. Para usar a funcionalidade de uma interface, você pode criar uma classe que implementa a interface ou derivar uma classe de uma das classes do .NET Framework que implementa a interface.  
  
## <a name="naming-conventions"></a>Convenções de nomenclatura  
 Os tipos do .NET Framework usam um esquema de nomenclatura de sintaxe por ponto que denota uma hierarquia. Essa técnica agrupa tipos relacionados em namespaces para que eles possam ser pesquisados e referenciados com mais facilidade. A primeira parte do nome completo — até o ponto mais à direita — é o nome do namespace. A última parte do nome é o nome do tipo. Por exemplo, **System.Collections.ArrayList** representa o tipo **ArrayList**, que pertence ao namespace **System.Collections**. Os tipos em **System.Collections** podem ser usados para manipular coleções de objetos.  
  
 Esse esquema de nomenclatura facilita para desenvolvedores de bibliotecas estender o [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] para criar grupos hierárquicos de tipos e nomeá-los de maneira consistente e informativa. Ele também permite que tipos sejam identificados sem ambiguidades por seu nome completo (ou seja, pelo namespace e pelo nome de tipo), o que impede conflitos de nomes de tipo. Os desenvolvedores de bibliotecas devem usar a seguinte convenção para criar nomes para seus namespaces:  
  
 *CompanyName*.*TechnologyName*  
  
 Por exemplo, o namespace Microsoft.Word está de acordo com essa diretriz.  
  
 O uso de padrões de nomenclatura para agrupar tipos relacionados em namespaces é uma forma muito útil de compilar e documentar bibliotecas de classes. No entanto, esse esquema de nomenclatura não afeta visibilidade, acesso a membro, herança, segurança ou associação. Um namespace pode ser particionado em vários assemblies e um único assembly pode conter tipos de vários namespaces. O assembly fornece a estrutura formal para criação de versão, implantação, segurança, carregamento e visibilidade no Common Language Runtime.  
  
 Para obter mais informações sobre namespaces e nomes de tipos, consulte [Common Type System](../../docs/standard/base-types/common-type-system.md).  
  
## <a name="system-namespace"></a>Namespace System  
 O <xref:System> é o namespace raiz para tipos fundamentais no [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]. Esse namespace contém classes que representam os tipos de dados base usados por todos os aplicativos: <xref:System.Object> (a raiz da hierarquia de herança), <xref:System.Byte>, <xref:System.Char>, <xref:System.Array>, <xref:System.Int32>, <xref:System.String> etc. Muitos desses tipos correspondem aos tipos de dados primitivos que sua linguagem de programação usa. Ao gravar códigos usando tipos .NET Framework, você pode usar a palavra-chave correspondente da sua linguagem quando um tipo de dados base do .NET Framework é esperado.  
  
 A tabela a seguir lista os tipos de base que o [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] fornece, descreve resumidamente cada tipo e indica o tipo correspondente em Visual Basic, C#, C++ e JScript.  
  
|Categoria|Nome da classe|Descrição|Tipo de dados em Visual Basic|Tipo de dados em C#|Tipo de dados em C++|Tipo de dados em JScript|  
|--------------|----------------|-----------------|----------------------------|-------------------|---------------------|-----------------------|  
|Inteiro|<xref:System.Byte>|Um inteiro de 8 bits sem sinal.|**Byte**|**byte**|**unsigned char**|**Byte**|  
||<xref:System.SByte>|Um inteiro de 8 bits com sinal.<br /><br /> Não compatível com CLS.|**SByte**|**sbyte**|**char**<br /><br /> -ou-<br /><br /> **signed** **char**|**SByte**|  
||<xref:System.Int16>|Um inteiro de 16 bits com sinal.|**Short**|**short**|**short**|**short**|  
||<xref:System.Int32>|Um inteiro com sinal de 32 bits.|**Integer**|**int**|**int**<br /><br /> -ou-<br /><br /> **long**|**int**|  
||<xref:System.Int64>|Um inteiro com sinal de 64 bits.|**Long**|**long**|**__int64**|**long**|  
||<xref:System.UInt16>|Um inteiro de 16 bits sem sinal.<br /><br /> Não compatível com CLS.|**UShort**|**ushort**|**unsigned short**|**UInt16**|  
||<xref:System.UInt32>|Um inteiro sem sinal de 32 bits.<br /><br /> Não compatível com CLS.|**UInteger**|**uint**|**unsigned int**<br /><br /> -ou-<br /><br /> **unsigned long**|**UInt32**|  
||<xref:System.UInt64>|Um inteiro sem sinal de 64 bits.<br /><br /> Não compatível com CLS.|**ULong**|**ulong**|**unsigned __int64**|**UInt64**|  
|Ponto flutuante|<xref:System.Single>|Um número de ponto flutuante de precisão simples (32 bits).|**Simples**|**float**|**float**|**float**|  
||<xref:System.Double>|Um número de ponto flutuante de precisão dupla (64 bits).|**Duplo**|**double**|**double**|**double**|  
|Lógico|<xref:System.Boolean>|Um valor booliano (verdadeiro ou falso).|**Booliano**|**bool**|**bool**|**bool**|  
|Outros|<xref:System.Char>|Um caractere Unicode (16 bits).|**Char**|**char**|**wchar_t**|**char**|  
||<xref:System.Decimal>|Um valor decimal (128 bits).|**Decimal**|**decimal**|**Decimal**|**Decimal**|  
||<xref:System.IntPtr>|Um inteiro com sinal cujo tamanho dependa da plataforma subjacente (um valor de 32 bits em uma plataforma de 32 bits e um valor de 64 bits em uma plataforma de 64 bits).|**IntPtr**<br /><br /> Nenhum tipo interno.|**IntPtr**<br /><br /> Nenhum tipo interno.|**IntPtr**<br /><br /> Nenhum tipo interno.|**IntPtr**|  
||<xref:System.UIntPtr>|Um inteiro sem sinal cujo tamanho dependa da plataforma subjacente (um valor de 32 bits em uma plataforma de 32 bits e um valor de 64 bits em uma plataforma de 64 bits).<br /><br /> Não compatível com CLS.|**UIntPtr**<br /><br /> Nenhum tipo interno.|**UIntPtr**<br /><br /> Nenhum tipo interno.|**UIntPtr**<br /><br /> Nenhum tipo interno.|**UIntPtr**|  
objetos ass|<xref:System.Object>|A raiz da hierarquia do objeto.|**Object**|**object**|**Object\***|**Object**|  
||<xref:System.String>|Uma cadeia de caracteres Unicode imutável e de comprimento fixo.|**Cadeia de caracteres**|**string**|**Cadeia de caracteres\***|**Cadeia de caracteres**|  
  
 Além dos tipos de dados base, o namespace <xref:System> contém mais de 100 classes, que vão desde classes que identificam exceções até classes que lidam com os conceitos de tempo de execução, como domínios de aplicativo e o coletor de lixo. O namespace <xref:System> também contém vários namespaces de segundo nível.  
  
 Para obter mais informações sobre namespaces, pesquise a [Biblioteca de classes .NET Framework](http://go.microsoft.com/fwlink/?LinkID=227195). Essa documentação de referência fornece uma visão geral resumida de cada namespace, bem como uma descrição formal de cada tipo e de seus membros.  
  
## <a name="see-also"></a>Consulte também  
 [Common Type System](../../docs/standard/base-types/common-type-system.md)   
 [Biblioteca de classes .NET Framework](http://go.microsoft.com/fwlink/?LinkID=227195)   
 [Visão Geral](../../docs/framework/get-started/overview.md)

