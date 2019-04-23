---
title: Configuração de atributos de assembly
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- assembly binding, attributes
- assembly manifest, attributes
ms.assetid: 36a98a81-b5b5-4c19-912a-11f91eff7f4e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6d07fe8ec61ee4515696eb3cf3d808483b50dfb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186557"
---
# <a name="setting-assembly-attributes"></a>Configuração de atributos de assembly
Os atributos de assembly são valores que fornecem informações sobre um assembly. Os atributos são divididos nos seguintes conjuntos de informações:  
  
-   Atributos de identidade do assembly.  
  
-   Atributos informativos.  
  
-   Atributos de manifesto do assembly.  
  
-   Atributos de nome forte.  
  
## <a name="assembly-identity-attributes"></a>Atributos de Identidade do Assembly  
 Três atributos, com um nome forte (se aplicável), determinam a identidade de um assembly: nome, versão e cultura. Esses atributos formam o nome completo do assembly e são necessários ao fazer referência ao assembly no código. Você pode usar atributos para definir a versão e a cultura de um assembly. O compilador ou o [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) define o valor do nome quando o assembly é criado, com base no arquivo que contém o manifesto do assembly.  
  
 A tabela a seguir descreve os atributos de versão e cultura.  
  
|Atributo de identidade do assembly|Descrição|  
|---------------------------------|-----------------|  
|<xref:System.Reflection.AssemblyCultureAttribute>|Campo enumerado que indica a cultura compatível com o assembly. Um assembly também pode especificar a independência da cultura, indicando que ela contém os recursos para a cultura padrão. **Observação:**  O tempo de execução trata como um assembly satélite qualquer assembly que não tenha o atributo de cultura definido como nulo. Esses assemblies estão sujeitos às regras de associação de assembly satélite. Para saber mais, confira [Como o tempo de execução localiza os assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).|  
|<xref:System.Reflection.AssemblyFlagsAttribute>|O valor que define os atributos de assembly; por exemplo, se o assembly pode ser executado lado a lado.|  
|<xref:System.Reflection.AssemblyVersionAttribute>|Valor numérico no formato *principal*.*secundário*.*compilação*.*revisão* (por exemplo, 2.4.0.0). O Common Language Runtime usa esse valor para executar operações de associação em assemblies com nome forte. **Observação:**  Se o atributo <xref:System.Reflection.AssemblyInformationalVersionAttribute> não for aplicado a um assembly, o número de versão especificado pelo atributo <xref:System.Reflection.AssemblyVersionAttribute> será usado pelas propriedades <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> e <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType>.|  
  
 O exemplo de código a seguir mostra como aplicar os atributos de versão e cultura a um assembly.  
  
 [!code-cpp[AssemblyDelaySignAttribute#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#3)]
 [!code-csharp[AssemblyDelaySignAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#3)]
 [!code-vb[AssemblyDelaySignAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#3)]  
  
## <a name="informational-attributes"></a>Atributos Informativos  
 Você pode usar atributos informativos para fornecer informações adicionais corporativas ou de produto para um assembly. A tabela a seguir descreve os atributos informativos que você pode aplicar a um assembly.  
  
|Atributos informativos|Descrição|  
|-----------------------------|-----------------|  
|<xref:System.Reflection.AssemblyCompanyAttribute>|O valor de cadeia de caracteres que especifica um nome de empresa.|  
|<xref:System.Reflection.AssemblyCopyrightAttribute>|O valor de cadeia de caracteres que especifica informações sobre direitos autorais.|  
|<xref:System.Reflection.AssemblyFileVersionAttribute>|O valor de cadeia de caracteres que especifica o número de versão do arquivo Win32. Isso normalmente tem como padrão a versão do assembly.|  
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|O valor de cadeia de caracteres que especifica informações de versão que não são usadas pelo Common Language Runtime, como o número de versão completo de um produto. **Observação:**  Se esse atributo for aplicado a um assembly, a cadeia de caracteres especificada por ele poderá ser obtida em tempo de execução usando a propriedade <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>. A cadeia de caracteres também é usada na chave do Registro e no caminho fornecidos pelas propriedades <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> e <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType>.|  
|<xref:System.Reflection.AssemblyProductAttribute>|O valor de cadeia de caracteres que especifica informações do produto.|  
|<xref:System.Reflection.AssemblyTrademarkAttribute>|O valor de cadeia de caracteres que especifica informações de marca registrada.|  
  
 Esses atributos podem aparecer na página Propriedades do Windows do assembly ou podem ser substituídos usando a opção de compilador **/win32res** para especificar seu próprio arquivo de recurso Win32.  
  
## <a name="assembly-manifest-attributes"></a>Atributos de Manifesto do Assembly  
 Também é possível usar atributos de manifesto do assembly para fornecer informações no manifesto do assembly, incluindo título, descrição, o alias padrão e a configuração. A tabela a seguir descreve os atributos de manifesto do assembly.  
  
|Atributo de manifesto do assembly|Descrição|  
|---------------------------------|-----------------|  
|<xref:System.Reflection.AssemblyConfigurationAttribute>|O valor de cadeia de caracteres que indica a configuração do assembly, como Retail ou Depuração. O tempo de execução não usa esse valor.|  
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|O valor de cadeia de caracteres que especifica um alias padrão a ser usado ao fazer referências de assemblies. Esse valor fornece um nome amigável quando o nome do assembly em si não o for (como um valor GUID). Esse valor também pode ser usado como uma forma abreviada do nome completo do assembly.|  
|<xref:System.Reflection.AssemblyDescriptionAttribute>|O valor de cadeia de caracteres que especifica uma breve descrição que resume a natureza e o objetivo do assembly.|  
|<xref:System.Reflection.AssemblyTitleAttribute>|O valor de cadeia de caracteres que especifica um nome amigável para o assembly. Por exemplo, um assembly denominado comdlg pode ter o título Controle de Diálogo Comum da Microsoft.|  
  
## <a name="strong-name-attributes"></a>Atributos de nome forte  
 Você pode usar atributos de nome forte para definir um nome forte para um assembly. A tabela a seguir descreve os atributos de nome forte.  
  
|Atributos de nome forte|Descrição|  
|----------------------------|-----------------|  
|<xref:System.Reflection.AssemblyDelaySignAttribute>|O valor booliano que indica que a assinatura em atraso está sendo usada.|  
|<xref:System.Reflection.AssemblyKeyFileAttribute>|O valor de cadeia de caracteres que indica o nome do arquivo que contém a chave pública (se usando assinatura em atraso) ou as chaves pública e privada passadas como um parâmetro ao construtor desse atributo. Observe que o nome de arquivo é relativo ao caminho do arquivo de saída (o .exe ou .dll), e não ao caminho do arquivo de origem.|  
|<xref:System.Reflection.AssemblyKeyNameAttribute>|Indica o contêiner de chaves que contém o par de chaves passado como um parâmetro ao construtor desse atributo.|  
  
 O exemplo de código a seguir mostra os atributos que se aplicam ao usar a assinatura em atraso para criar um assembly de nome forte com um arquivo de chave pública chamado `myKey.snk`.  
  
 [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
 [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
 [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
## <a name="see-also"></a>Consulte também

- [Criação de assemblies](../../../docs/framework/app-domains/create-assemblies.md)
- [Programação com assemblies](../../../docs/framework/app-domains/programming-with-assemblies.md)
