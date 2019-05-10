---
title: Palavras-chave e níveis ETW no CLR
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW keywords
- CLR ETW levels
- ETW, CLR keywords
- ETW, CLR levels
ms.assetid: fdf5856d-516b-4042-849d-911c4518a6cb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9a9061503ae4bf68903f35eb7624deed2f34c9b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616607"
---
# <a name="clr-etw-keywords-and-levels"></a>Palavras-chave e níveis ETW no CLR
<a name="top"></a> Os eventos ETW (rastreamento de eventos para Windows) pode ser filtrado por categoria e nível. As [palavras-chave CLR ETW](#keywords) do evento permitem a filtragem de eventos por categoria; elas são usadas em combinações para os provedores de tempo de execução e de encerramento. Os [níveis de evento](#levels) são identificados por sinalizadores.  
  
<a name="keywords"></a>   
## <a name="clr-etw-keywords"></a>Palavras-chave CLR ETW  
 As palavras-chave são sinalizadores que podem ser combinados para gerar valores. Na prática, você usa os valores hexadecimais das palavras-chave, em vez dos nomes da palavra-chave, ao chamar os utilitários de linha de comando.  
  
 Essas palavras-chave são descritas nas seguintes tabelas:  
  
- [Palavras-chave de tempo de execução CLR ETW](#runtime)  
  
- [Palavras-chave de encerramento CLR ETW](#rundown)  
  
- [Combinações de palavras-chave para a resolução de símbolo do provedor de tempo de execução](#runtime_combo)  
  
- [Combinações de palavras-chave para a resolução de símbolo do provedor de encerramento](#rundown_combo)  
  
<a name="runtime"></a>   
### <a name="clr-etw-runtime-keywords"></a>Palavras-Chave de Tempo de Execução CLR ETW  
 A tabela a seguir lista as palavras-chave de tempo de execução CLR ETW, seus valores e sua finalidade de uso.  
  
|Nome da palavra-chave de tempo de execução|Valor|Finalidade|  
|--------------------------|-----------|-------------|  
|`GCKeyword`|0x00000001|Habilita a coleta de [eventos de coleta de lixo](../../../docs/framework/performance/garbage-collection-etw-events.md).|  
|`LoaderKeyword`|0x00000008|Habilita a coleta de [eventos de carregador](../../../docs/framework/performance/loader-etw-events.md).|  
|`JITKeyword`|0x00000010|Habilita a coleta de [eventos JIT (Just-In-Time)](../../../docs/framework/performance/jit-tracing-etw-events.md).|  
|`NGenKeyword`|0x00000020|Habilita a coleta de eventos de métodos de imagem nativa (métodos processados pelo Gerador de Imagem Nativa, Ngen.exe); usado com `StartEnumerationKeyword` e `EndEnumerationKeyword`. Essa palavra-chave tem uma alta sobrecarga. Ela gera eventos para cada método dentro de cada módulo do NGen carregado. Sempre que possível, em vez de usar essa palavra-chave, recomendamos o uso dos PDBs (bancos de dados do programa) gerados pelas ferramentas de criação de perfil para recuperar informações sobre os métodos dos módulos do NGen. Consulte também `OverrideAndSuppressNGenEventsKeyword` mais adiante nesta tabela.|  
|`StartEnumerationKeyword`|0x00000040|Habilita a enumeração de todos os métodos no tempo de execução; usado em conjunto com `NGenKeyword`.|  
|`EndEnumerationKeyword`|0x00000080|Habilita a enumeração de todos os métodos destruídos no tempo de execução; usado em conjunto com `JITKeyword` e `NGenKeyword`.|  
|`SecurityKeyword`|0x00000400|Habilita a coleta de [eventos de segurança](../../../docs/framework/performance/security-etw-events.md).|  
|`AppDomainResourceManagementKeyword`|0x00000800|Habilita a coleção de eventos de monitoramento de recursos no nível de um domínio do aplicativo.|  
|`JITTracingKeyword`|0x00001000|Habilita a coleta de [eventos de rastreamento JIT](../../../docs/framework/performance/jit-tracing-etw-events.md).|  
|`InteropKeyword`|0x00002000|Habilita a coleta de [eventos de interoperabilidade](../../../docs/framework/performance/interop-etw-events.md).|  
|`ContentionKeyword`|0x00004000|Habilita a coleta de [eventos de contenção](../../../docs/framework/performance/contention-etw-events.md).|  
|`ExceptionKeyword`|0x00008000|Habilita a coleta de [eventos de exceção](../../../docs/framework/performance/exception-thrown-v1-etw-event.md).|  
|`ThreadingKeyword`|0x00010000|Habilita a coleta de [eventos de pool de threads](../../../docs/framework/performance/thread-pool-etw-events.md).|  
|`OverrideAndSuppressNGenEventsKeyword`|0x00040000|(Disponível no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] e posterior.) Suprime a palavra-chave `NGenKeyword` de alta sobrecarga e impede a geração de eventos para os métodos que estão dentro dos módulos do NGen. A partir do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], as ferramentas de criação de perfil devem usar `OverrideAndSuppressNGenEventsKeyword` e `NGenKeyword` em conjunto para suprimir a geração de eventos para os métodos nos módulos do NGen. Isso permite que a ferramenta de criação de perfil use os PDBs mais eficientes do NGen para obter informações sobre os métodos nos módulos do NGen. O CLR no .NET Framework 4 e versões anteriores não dá suporte à criação de PDBs do NGen. Nessas versões anteriores, o CLR não reconhecerá `OverrideAndSuppressNGenEventsKeyword` e processará `NGenKeyword` para gerar eventos para os métodos nos módulos do NGen.|  
|`PerfTrackKeyWord`|0x2000000|Habilita a coleta dos eventos `ModuleLoad` e `ModuleRange`.|  
|`StackKeyword`|0x40000000|Habilita a coleta de [eventos de rastreamento de pilha](../../../docs/framework/performance/stack-etw-event.md) do CLR.|  
  
 [Voltar ao início](#top)  
  
<a name="rundown"></a>   
### <a name="clr-etw-rundown-keywords"></a>Palavras-Chave de Encerramento CLR ETW  
 A tabela a seguir lista as palavras-chave de encerramento CLR ETW, seus valores e sua finalidade de uso.  
  
|Nome da palavra-chave de encerramento|Valor|Finalidade|  
|--------------------------|-----------|-------------|  
|`LoaderRundownKeyword`|0x00000008|Habilita a coleta de eventos de carregador quando usado com `StartRundownKeyword` e `EndRundownKeyword`.|  
|`JitRundownKeyword`|0x00000010|Habilita a coleta dos eventos `DCStart` e `DCEnd` do método para métodos compilados pelo JIT quando usado com `StartRundownKeyword` e `EndRundownKeyword`.|  
|`NGenRundownKeyword`|0x00000020|Habilita a coleta dos eventos `DCStart` e `DCEnd` do método para métodos de imagem nativa do NGen quando usado com `StartRundownKeyword` e `EndRundownKeyword`. Essa palavra-chave tem uma alta sobrecarga. Ela gera eventos para cada método dentro de cada módulo do NGen carregado. Sempre que possível, em vez de usar essa palavra-chave, recomendamos o uso dos PDBs (bancos de dados do programa) gerados pelas ferramentas de criação de perfil para recuperar informações sobre os métodos dos módulos do NGen. Consulte também `OverrideAndSuppressNGenEventsRundownKeyword` mais adiante nesta tabela.|  
|`StartRundownKeyword`|0x00000040|Habilita a enumeração de estado do sistema durante um encerramento inicial.|  
|`EndRundownKeyword`|0x00000100|Habilita a enumeração de estado do sistema durante um encerramento final.|  
|`AppDomainResourceManagementRundownKeyword`|0x00000800|Habilita a coleta de eventos de monitoramento de recursos no nível de um <xref:System.AppDomain> quando usado com `StartRundownKeyword` ou `EndRundownKeyword`.|  
|`ThreadingKeyword`|0x00010000|Habilita a coleta de eventos de pool de threads.|  
|`OverrideAndSuppressNGenEventsRundownKeyword`|0x00040000|(Disponível no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] e posterior.) Suprime a palavra-chave `NGenRundownKeyword` de alta sobrecarga e impede a geração de eventos para os métodos que estão dentro dos módulos do NGen. A partir do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], as ferramentas de criação de perfil devem usar `OverrideAndSuppressNGenEventsRundownKeyword` e `NGenRundownKeyword` em conjunto para suprimir a geração de eventos para os métodos nos módulos do NGen. Isso permite que a ferramenta de criação de perfil use os PDBs mais eficientes do NGen para obter informações sobre os métodos nos módulos do NGen. O CLR no .NET Framework 4 e versões anteriores não dá suporte à criação de PDBs do NGen. Nessas versões anteriores, o CLR não reconhecerá `OverrideAndSuppressNGenEventsRundownKeyword` e processará `NGenRundownKeyword` para gerar eventos para os métodos nos módulos do NGen.|  
|`PerfTrackKeyWord`|0x2000000|Habilita a coleta dos eventos `ModuleDCStart`, `ModuleDCEnd`, `ModuleRangeDCStart` e `ModuleRangeDCEnd`.|  
  
 [Voltar ao início](#top)  
  
<a name="runtime_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-runtime-provider"></a>Combinações de palavras-chave para a resolução de símbolo do provedor de tempo de execução  
  
|Palavras-chave e sinalizadores|Domínio do aplicativo, assembly, eventos de carregamento/descarregamento do módulo|Eventos de carregamento/descarregamento do método (exceto eventos dinâmicos)|Eventos de carregamento/destruição de método dinâmico|  
|------------------------|--------------------------------------------------------------|----------------------------------------------------------|-----------------------------------------|  
|`LoaderKeyword`|Eventos de carregamento e descarregamento.|nenhuma.|nenhuma.|  
|`JITKeyword`<br /><br /> (+ `StartEnumerationKeyword` não adiciona nada)|nenhuma.|Eventos de carregamento.|Eventos de carregamento e descarregamento.|  
|`JITKeyword` +<br /><br /> `EndEnumerationKeyword`|nenhuma.|Eventos de carregamento e descarregamento.|Eventos de carregamento e descarregamento.|  
|`NGenKeyword`|nenhuma.|nenhuma.|Não aplicável.|  
|`NGenKeyword` +<br /><br /> `StartEnumerationKeyword`|nenhuma.|Eventos de carregamento.|Não aplicável.|  
|`NGenKeyword` +<br /><br /> `EndEnumerationKeyword`|nenhuma.|Eventos de descarregamento.|Não aplicável.|  
  
 [Voltar ao início](#top)  
  
<a name="rundown_combo"></a>   
### <a name="keyword-combinations-for-symbol-resolution-for-the-rundown-provider"></a>Combinações de palavras-chave para a resolução de símbolo do provedor de encerramento  
  
|Palavras-chave e sinalizadores|Domínio do aplicativo, assembly, eventos de DCStart/DCEnd do módulo|Eventos de DCStart/DCEnd do módulo (incluindo eventos de método dinâmico)|  
|------------------------|----------------------------------------------------------------|----------------------------------------------------------------------|  
|`LoaderRundownKeyword` +<br /><br /> `StartRundownKeyword`|Eventos `DCStart`.|nenhuma.|  
|`LoaderRundownKeyword` +<br /><br /> `EndRundownKeyword`|Eventos `DCEnd`.|nenhuma.|  
|`JITKeyword` +<br /><br /> `StartRundownKeyword`|nenhuma.|Eventos `DCStart`.|  
|`JITKeyword` +<br /><br /> `EndRundownKeyword`|nenhuma.|Eventos `DCEnd`.|  
|`NGenKeyword` +<br /><br /> `StartRundownKeyword`|nenhuma.|Eventos `DCStart`.|  
|`NGenKeyword` +<br /><br /> `EndRundownKeyword`|nenhuma.|Eventos `DCEnd`.|  
  
 [Voltar ao início](#top)  
  
<a name="levels"></a>   
## <a name="etw-event-levels"></a>Níveis de eventos ETW  
 Os eventos ETW também podem ser filtrados por nível. Se o nível for definido como 0x5, eventos de todos os níveis serão acionados, incluindo 0x5 e abaixo (que são eventos que pertencem às categorias habilitadas por meio de palavras-chave). Se o nível for definido como 0x2, somente os eventos que pertencem ao nível 0x2 e abaixo serão acionados.  
  
 Os níveis têm os seguintes significados:  
  
 0x5 – Detalhado  
  
 0x4 – Informativo  
  
 0x3 – Aviso  
  
 0x2 – Erro  
  
 0x1 – Crítico  
  
 0x0 – LogAlways  
  
## <a name="see-also"></a>Consulte também

- [Provedores CLR ETW](../../../docs/framework/performance/clr-etw-providers.md)
- [Eventos de CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
- [Eventos ETW no Common Language Runtime](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
