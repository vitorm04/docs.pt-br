---
title: Executando aplicativos de intranet em confiança total
ms.date: 03/30/2017
helpviewer_keywords:
- full trust, running intranet applications in
- intranet applications, running in full trust
- running intranet applications in full trust
ms.assetid: ee13c0a8-ab02-49f7-b8fb-9eab16c6c4f0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1996c8b317bbfed6362c759a257cafef8400e919
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70971905"
---
# <a name="running-intranet-applications-in-full-trust"></a>Executando aplicativos de intranet em confiança total
A partir do .NET Framework versão 3.5 SP1 (Service Pack 1), os aplicativos e seus assemblies de bibliotecas podem ser executados como assemblies de confiança total de um compartilhamento de rede. A evidência de zona <xref:System.Security.SecurityZone.MyComputer> é automaticamente adicionada a assemblies que são carregados de um compartilhamento na intranet. Essa evidência fornece a esses assemblies o mesmo conjunto de concessões (que geralmente é de confiança total) que os assemblies que residem no computador. Essa funcionalidade não se aplica aos aplicativos ClickOnce ou que são projetados para serem executados em um host.  
  
## <a name="rules-for-library-assemblies"></a>Regras para assemblies de bibliotecas  
 As seguintes regras se aplicam a assemblies que são carregados por um executável em um compartilhamento de rede:  
  
- Os assemblies de bibliotecas devem residir na mesma pasta do assembly executável. Os assemblies que residem em uma subpasta ou são referenciados em um caminho diferente não recebem o conjunto de concessões de confiança total.  
  
- Se o executável carregar um assembly com atraso, ele deverá usar o mesmo caminho que foi usado para iniciar o executável. Por exemplo, se o compartilhamento \\\\*computador da rede*\\*compartilhamento* for mapeado para uma letra da unidade e o executável for executado a partir desse caminho, os assemblies que forem carregados pelo executável usando o caminho de rede não receberão confiança total. Para carregar um assembly com atraso na zona <xref:System.Security.SecurityZone.MyComputer>, o executável deve usar o caminho da letra da unidade.  
  
## <a name="restoring-the-former-intranet-policy"></a>Restauração da política antiga de intranet  
 Em versões anteriores do .NET Framework, os assemblies compartilhados recebiam a evidência de zona <xref:System.Security.SecurityZone.Intranet>. Era preciso especificar a política de segurança de acesso do código para conceder confiança total a um assembly em um compartilhamento.  
  
 Esse novo comportamento é o padrão para assemblies da intranet. Você pode retornar ao comportamento anterior fornecendo a evidência <xref:System.Security.SecurityZone.Intranet> ao configurar uma chave do Registro que se aplica a todos os aplicativos no computador. Esse processo é diferente para computadores de 32 bits e 64 bits:  
  
- Em computadores de 32 bits, crie uma subchave sob a chave HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework no Registro do sistema. Use o nome de chave LegacyMyComputerZone com um valor DWORD de 1.  
  
- Em computadores de 64 bits, crie uma subchave sob a chave HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework no Registro do sistema. Use o nome de chave LegacyMyComputerZone com um valor DWORD de 1. Crie a mesma subchave sob a chave HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework.  
  
## <a name="see-also"></a>Consulte também

- [Programação com assemblies](../../standard/assembly/program.md)
