---
title: Diretiva x:FieldModifier
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 27ff9d027f5ff5155543097b7f0f0c2839387fe5
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58042445"
---
# <a name="xfieldmodifier-directive"></a>Diretiva x:FieldModifier
Modifica o comportamento de compilação de XAML para que os campos para referências de objeto nomeado são definidos com <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> acessar em vez do <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> comportamento padrão.  
  
## <a name="xaml-attribute-usage"></a>Uso do Atributo XAML  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a>Valores XAML  
  
|||  
|-|-|  
|*Público*|A cadeia de caracteres exata que você passa para especificar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> versus <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> varia, dependendo da linguagem de programação de lógica que é usada. Consulte Observações.|  
  
## <a name="dependencies"></a>Dependências  
 Se usar uma produção de XAML `x:FieldModifier` em qualquer lugar, o elemento raiz de produção que XAML deve declarar um [diretiva X:Class](x-class-directive.md).  
  
## <a name="remarks"></a>Comentários  
 `x:FieldModifier` não é relevante para declarar o nível de acesso geral de uma classe ou seus membros. Ele é relevante apenas para o comportamento de processamento de XAML quando um objeto específico de XAML que faz parte de uma produção de XAML é processado e se torna um objeto que é potencialmente acessível no grafo de objeto de um aplicativo. Por padrão, a referência de campo para esse objeto é mantida privada, que impede que os consumidores de controle de modificar diretamente o grafo de objeto. Em vez disso, os consumidores de controle são esperados para modificar o gráfico do objeto, usando padrões que são habilitados por modelos de programação, como ao obter a raiz de layout filho coleções de elementos, as propriedades públicas dedicadas, e assim por diante.  
  
 O valor para o `x:FieldModifier` atributo varia por linguagem de programação e sua finalidade pode variar em estruturas específicas. A cadeia de caracteres a ser usado depende de como cada linguagem implementa sua <xref:System.CodeDom.Compiler.CodeDomProvider> e os conversores de tipo, ele retorna para definir os significados para <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> e <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, e se esse idioma é diferencia maiusculas de minúsculas.  
  
-   Para c#, a cadeia de caracteres para passar para designar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> é `public`.  
  
-   Para o Microsoft Visual Basic .NET, a cadeia de caracteres para passar para designar <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> é `Public`.  
  
-   Para [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)], nenhum destino para XAML existe no momento; portanto, para passar a cadeia de caracteres é indefinida.  
  
 Você também pode especificar <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> (`internal` em C#, `Friend` no Visual Basic), mas especificando <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> é incomum porque `NotPublic` como o comportamento já é o padrão.  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> é o comportamento padrão porque é raro que código fora do assembly compilado a XAML precisa de acesso a um elemento criado em XAML. Arquitetura de segurança junto com o comportamento de compilação XAML do WPF não declarar campos que armazenam as instâncias de elementos como pública, a menos que você defina especificamente o `x:FieldModifier` para permitir acesso público.  
  
 `x:FieldModifier` só é relevante para elementos com um [X:Name Directive](x-name-directive.md) porque esse nome é usado para referenciar o campo depois que ele é público.  
  
 Por padrão, a classe parcial para o elemento raiz é pública; No entanto, você pode torná-lo não públicos usando o [diretiva X:ClassModifier](x-classmodifier-directive.md). O [diretiva X:ClassModifier](x-classmodifier-directive.md) também afeta o nível de acesso da instância da classe de elemento raiz. Você pode colocar ambos `x:Name` e `x:FieldModifier` na raiz do elemento, mas isso só faz uma cópia do campo público do elemento raiz, com o raiz true elemento classe nível de acesso ainda controlada pelo [diretiva X:ClassModifier](x-classmodifier-directive.md).  
  
## <a name="see-also"></a>Consulte também
- [XAML e classes personalizadas para WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Code-behind e XAML no WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [Diretiva x:Name](x-name-directive.md)
- [Como compilar um aplicativo WPF (WPF)](../wpf/app-development/building-a-wpf-application-wpf.md)
- [Diretiva x:ClassModifier](x-classmodifier-directive.md)
