---
title: "Mitigação: controle de versão de produto | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
caps.latest.revision: 15
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a6bf9656dee0e6074a8341997abb0e73dc3666f5
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-product-versioning"></a>Mitigação: Controle de versão de produto
Na [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] e posterior, o controle de versão de produto foi alterada em relação às versões anteriores do .NET Framework (o .NET Framework 4, 4.5, 4.5.1 e 4.5.2).  
  
## <a name="product-versioning-changes"></a>Alterações no controle de versão de produto  
 Veja a seguir as alterações em detalhes:  
  
-   O valor da entrada `Version` na chave `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` foi alterado para `4.6.`*xxxxx* para o .NET Framework 4.6 e suas versões pontuais, e para `4.7.`*xxxxx* para o .NET Framework 4.7. No .NET Framework 4.5, 4.5.1 e 4.5.2, ele tinha o formato `4.5.`*xxxxx*.  
  
-   O controle de versão de arquivo e produto para arquivos do .NET Framework foi alterado do esquema de controle de versão anterior de `4.0.30319.x` para o de `4.6.X.0` para o .NET Framework 4.6 e suas versões pontuais, e para o de `4.7.X.0` para o .NET Framework 4.7 e suas versões pontuais. Você pode ver esses novos valores quando exibe as **Propriedades** do arquivo depois de clicar com o botão direito do mouse em um arquivo.  
  
-   Os atributos <xref:System.Reflection.AssemblyFileVersionAttribute> e <xref:System.Reflection.AssemblyInformationalVersionAttribute> para assemblies gerenciados têm valores <xref:System.Version> na forma `4.6.X.0` para o .NET Framework 4.6 e suas versões pontuais, e `4.7.X.0` para o .NET Framework 4.7.  
  
-   No [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2 e 4.7, a propriedade <xref:System.Environment.Version%2A?displayProperty=fullName> retorna a cadeia de caracteres de versão fixa `4.0.30319.42000`. No .NET Framework 4, 4.5, 4.5.1 e 4.5.2, ela retorna as cadeias de caracteres de versão no formato `4.0.30319.xxxxx` (por exemplo, "4.0.30319.18010"). Observe que não é recomendável que o código de aplicativo obtenha qualquer nova dependência na propriedade <xref:System.Environment.Version%2A?displayProperty=fullName>.  
  
### <a name="handling-the-product-versioning-changes"></a>Como lidar com as alterações de controle de versão de produto  
 Em geral, os aplicativos devem depender das técnicas recomendadas para detecção de itens como a versão de tempo de execução do .NET Framework e o diretório de instalação:  
  
-   Para detectar a versão de tempo de execução do .NET Framework, confira [How to: Determine Which .NET Framework Versions Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md) (Como determinar quais versões do .NET Framework estão instaladas).  
  
-   Para determinar o caminho de instalação do .NET Framework, use o valor da entrada `InstallPath` na chave `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`.  
  
    > [!IMPORTANT]
    >  O nome da subchave é `NET Framework Setup`, e não `.NET Framework Setup`.  
  
-   Para determinar o caminho do diretório para o Common Language Runtime do .NET Framework, chame o método <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=fullName>.  
  
-   Para obter a versão do CLR, chame o método <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=fullName>.   Para o .NET Framework 4 e suas versões pontuais (o .NET Framework 4.5, 4.5.1, 4.5.2 e [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2 e 4.7), ele retorna a cadeia de caracteres `v4.0.30319`.  
  
## <a name="see-also"></a>Consulte também  
 [Alterações no tempo de execução](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
 
