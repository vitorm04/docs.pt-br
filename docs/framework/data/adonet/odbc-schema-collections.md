---
title: Coleções de esquema ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: bdedbb11960f02b99dcca6388abf663635238f74
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43750003"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="c6da7-102">Coleções de esquema ODBC</span><span class="sxs-lookup"><span data-stu-id="c6da7-102">ODBC Schema Collections</span></span>
<span data-ttu-id="c6da7-103">Esta seção discute o suporte de coleção de esquema para os drivers ODBC para Microsoft SQL Server, Oracle e Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="c6da7-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="c6da7-104">Driver ODBC do Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="c6da7-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="c6da7-105">O Driver ODBC do Microsoft SQL Server suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="c6da7-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="c6da7-106">Tabelas</span><span class="sxs-lookup"><span data-stu-id="c6da7-106">Tables</span></span>  
  
-   <span data-ttu-id="c6da7-107">Índices</span><span class="sxs-lookup"><span data-stu-id="c6da7-107">Indexes</span></span>  
  
-   <span data-ttu-id="c6da7-108">Colunas</span><span class="sxs-lookup"><span data-stu-id="c6da7-108">Columns</span></span>  
  
-   <span data-ttu-id="c6da7-109">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="c6da7-109">Procedures</span></span>  
  
-   <span data-ttu-id="c6da7-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="c6da7-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="c6da7-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="c6da7-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="c6da7-112">Exibições</span><span class="sxs-lookup"><span data-stu-id="c6da7-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="c6da7-113">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="c6da7-113">Tables and Views</span></span>  
  
|<span data-ttu-id="c6da7-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c6da7-114">ColumnName</span></span>|<span data-ttu-id="c6da7-115">DataType</span><span class="sxs-lookup"><span data-stu-id="c6da7-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6da7-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="c6da7-116">TABLE_CAT</span></span>|<span data-ttu-id="c6da7-117">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-117">String</span></span>|  
|<span data-ttu-id="c6da7-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="c6da7-118">TABLE_SCHEM</span></span>|<span data-ttu-id="c6da7-119">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-119">String</span></span>|  
|<span data-ttu-id="c6da7-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-120">TABLE_NAME</span></span>|<span data-ttu-id="c6da7-121">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-121">String</span></span>|  
|<span data-ttu-id="c6da7-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-122">TABLE_TYPE</span></span>|<span data-ttu-id="c6da7-123">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-123">String</span></span>|  
|<span data-ttu-id="c6da7-124">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="c6da7-124">REMARKS</span></span>|<span data-ttu-id="c6da7-125">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="c6da7-126">Índices</span><span class="sxs-lookup"><span data-stu-id="c6da7-126">Indexes</span></span>  
  
|<span data-ttu-id="c6da7-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c6da7-127">ColumnName</span></span>|<span data-ttu-id="c6da7-128">DataType</span><span class="sxs-lookup"><span data-stu-id="c6da7-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6da7-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="c6da7-129">TABLE_CAT</span></span>|<span data-ttu-id="c6da7-130">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-130">String</span></span>|  
|<span data-ttu-id="c6da7-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="c6da7-131">TABLE_SCHEM</span></span>|<span data-ttu-id="c6da7-132">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-132">String</span></span>|  
|<span data-ttu-id="c6da7-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-133">TABLE_NAME</span></span>|<span data-ttu-id="c6da7-134">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-134">String</span></span>|  
|<span data-ttu-id="c6da7-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="c6da7-135">NON_UNIQUE</span></span>|<span data-ttu-id="c6da7-136">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-136">Int16</span></span>|  
|<span data-ttu-id="c6da7-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c6da7-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="c6da7-138">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-138">String</span></span>|  
|<span data-ttu-id="c6da7-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-139">INDEX_NAME</span></span>|<span data-ttu-id="c6da7-140">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-140">String</span></span>|  
|<span data-ttu-id="c6da7-141">TIPO</span><span class="sxs-lookup"><span data-stu-id="c6da7-141">TYPE</span></span>|<span data-ttu-id="c6da7-142">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-142">Int16</span></span>|  
|<span data-ttu-id="c6da7-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c6da7-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="c6da7-144">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-144">Int16</span></span>|  
|<span data-ttu-id="c6da7-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-145">COLUMN_NAME</span></span>|<span data-ttu-id="c6da7-146">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-146">String</span></span>|  
|<span data-ttu-id="c6da7-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="c6da7-147">ASC_OR_DESC</span></span>|<span data-ttu-id="c6da7-148">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-148">String</span></span>|  
|<span data-ttu-id="c6da7-149">CARDINALIDADE</span><span class="sxs-lookup"><span data-stu-id="c6da7-149">CARDINATLITY</span></span>|<span data-ttu-id="c6da7-150">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-150">Int32</span></span>|  
|<span data-ttu-id="c6da7-151">PÁGINAS</span><span class="sxs-lookup"><span data-stu-id="c6da7-151">PAGES</span></span>|<span data-ttu-id="c6da7-152">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-152">Int32</span></span>|  
|<span data-ttu-id="c6da7-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="c6da7-153">FILTER_CONDITION</span></span>|<span data-ttu-id="c6da7-154">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-154">String</span></span>|  
|<span data-ttu-id="c6da7-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c6da7-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="c6da7-156">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-156">String</span></span>|  
|<span data-ttu-id="c6da7-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="c6da7-158">Byte</span><span class="sxs-lookup"><span data-stu-id="c6da7-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="c6da7-159">Colunas</span><span class="sxs-lookup"><span data-stu-id="c6da7-159">Columns</span></span>  
  
|<span data-ttu-id="c6da7-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c6da7-160">ColumnName</span></span>|<span data-ttu-id="c6da7-161">DataType</span><span class="sxs-lookup"><span data-stu-id="c6da7-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6da7-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="c6da7-162">TABLE_CAT</span></span>|<span data-ttu-id="c6da7-163">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-163">String</span></span>|  
|<span data-ttu-id="c6da7-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="c6da7-164">TABLE_SCHEM</span></span>|<span data-ttu-id="c6da7-165">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-165">String</span></span>|  
|<span data-ttu-id="c6da7-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-166">TABLE_NAME</span></span>|<span data-ttu-id="c6da7-167">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-167">String</span></span>|  
|<span data-ttu-id="c6da7-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-168">COLUMN_NAME</span></span>|<span data-ttu-id="c6da7-169">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-169">String</span></span>|  
|<span data-ttu-id="c6da7-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-170">DATA_TYPE</span></span>|<span data-ttu-id="c6da7-171">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-171">Int16</span></span>|  
|<span data-ttu-id="c6da7-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-172">TYPE_NAME</span></span>|<span data-ttu-id="c6da7-173">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-173">String</span></span>|  
|<span data-ttu-id="c6da7-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="c6da7-174">COLUMN_SIZE</span></span>|<span data-ttu-id="c6da7-175">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-175">Int32</span></span>|  
|<span data-ttu-id="c6da7-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c6da7-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="c6da7-177">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-177">Int32</span></span>|  
|<span data-ttu-id="c6da7-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="c6da7-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="c6da7-179">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-179">Int16</span></span>|  
|<span data-ttu-id="c6da7-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="c6da7-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="c6da7-181">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-181">Int16</span></span>|  
|<span data-ttu-id="c6da7-182">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="c6da7-182">NULLABLE</span></span>|<span data-ttu-id="c6da7-183">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-183">Int16</span></span>|  
|<span data-ttu-id="c6da7-184">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="c6da7-184">REMARKS</span></span>|<span data-ttu-id="c6da7-185">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-185">String</span></span>|  
|<span data-ttu-id="c6da7-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="c6da7-186">COLUMN_DEF</span></span>|<span data-ttu-id="c6da7-187">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-187">String</span></span>|  
|<span data-ttu-id="c6da7-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="c6da7-189">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-189">Int16</span></span>|  
|<span data-ttu-id="c6da7-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="c6da7-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="c6da7-191">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-191">Int16</span></span>|  
|<span data-ttu-id="c6da7-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c6da7-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="c6da7-193">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-193">Int32</span></span>|  
|<span data-ttu-id="c6da7-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c6da7-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="c6da7-195">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-195">Int32</span></span>|  
|<span data-ttu-id="c6da7-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="c6da7-196">IS_NULLABLE</span></span>|<span data-ttu-id="c6da7-197">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-197">String</span></span>|  
|<span data-ttu-id="c6da7-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c6da7-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="c6da7-199">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-199">String</span></span>|  
|<span data-ttu-id="c6da7-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c6da7-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="c6da7-201">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-201">String</span></span>|  
|<span data-ttu-id="c6da7-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="c6da7-203">Byte</span><span class="sxs-lookup"><span data-stu-id="c6da7-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="c6da7-204">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="c6da7-204">Procedures</span></span>  
  
|<span data-ttu-id="c6da7-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c6da7-205">ColumnName</span></span>|<span data-ttu-id="c6da7-206">DataType</span><span class="sxs-lookup"><span data-stu-id="c6da7-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6da7-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="c6da7-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="c6da7-208">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-208">String</span></span>|  
|<span data-ttu-id="c6da7-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="c6da7-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="c6da7-210">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-210">String</span></span>|  
|<span data-ttu-id="c6da7-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="c6da7-212">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-212">String</span></span>|  
|<span data-ttu-id="c6da7-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="c6da7-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="c6da7-214">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-214">Int32</span></span>|  
|<span data-ttu-id="c6da7-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="c6da7-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="c6da7-216">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-216">Int32</span></span>|  
|<span data-ttu-id="c6da7-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="c6da7-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="c6da7-218">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-218">Int32</span></span>|  
|<span data-ttu-id="c6da7-219">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="c6da7-219">REMARKS</span></span>|<span data-ttu-id="c6da7-220">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-220">String</span></span>|  
|<span data-ttu-id="c6da7-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="c6da7-222">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="c6da7-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="c6da7-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="c6da7-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c6da7-224">ColumnName</span></span>|<span data-ttu-id="c6da7-225">DataType</span><span class="sxs-lookup"><span data-stu-id="c6da7-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6da7-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="c6da7-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="c6da7-227">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-227">String</span></span>|  
|<span data-ttu-id="c6da7-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="c6da7-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="c6da7-229">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-229">String</span></span>|  
|<span data-ttu-id="c6da7-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="c6da7-231">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-231">String</span></span>|  
|<span data-ttu-id="c6da7-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-232">COLUMN_NAME</span></span>|<span data-ttu-id="c6da7-233">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-233">String</span></span>|  
|<span data-ttu-id="c6da7-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-234">COLUMN_TYPE</span></span>|<span data-ttu-id="c6da7-235">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-235">Int16</span></span>|  
|<span data-ttu-id="c6da7-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-236">DATA_TYPE</span></span>|<span data-ttu-id="c6da7-237">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-237">Int16</span></span>|  
|<span data-ttu-id="c6da7-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-238">TYPE_NAME</span></span>|<span data-ttu-id="c6da7-239">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-239">String</span></span>|  
|<span data-ttu-id="c6da7-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="c6da7-240">COLUMN_SIZE</span></span>|<span data-ttu-id="c6da7-241">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-241">Int32</span></span>|  
|<span data-ttu-id="c6da7-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c6da7-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="c6da7-243">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-243">Int32</span></span>|  
|<span data-ttu-id="c6da7-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="c6da7-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="c6da7-245">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-245">Int16</span></span>|  
|<span data-ttu-id="c6da7-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="c6da7-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="c6da7-247">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-247">Int16</span></span>|  
|<span data-ttu-id="c6da7-248">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="c6da7-248">NULLABLE</span></span>|<span data-ttu-id="c6da7-249">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-249">Int16</span></span>|  
|<span data-ttu-id="c6da7-250">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="c6da7-250">REMARKS</span></span>|<span data-ttu-id="c6da7-251">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-251">String</span></span>|  
|<span data-ttu-id="c6da7-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="c6da7-252">COLUMN_DEF</span></span>|<span data-ttu-id="c6da7-253">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-253">String</span></span>|  
|<span data-ttu-id="c6da7-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="c6da7-255">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-255">Int16</span></span>|  
|<span data-ttu-id="c6da7-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="c6da7-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="c6da7-257">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-257">Int16</span></span>|  
|<span data-ttu-id="c6da7-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c6da7-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="c6da7-259">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-259">Int32</span></span>|  
|<span data-ttu-id="c6da7-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c6da7-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="c6da7-261">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-261">Int32</span></span>|  
|<span data-ttu-id="c6da7-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="c6da7-262">IS_NULLABLE</span></span>|<span data-ttu-id="c6da7-263">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-263">String</span></span>|  
|<span data-ttu-id="c6da7-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c6da7-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="c6da7-265">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-265">String</span></span>|  
|<span data-ttu-id="c6da7-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c6da7-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="c6da7-267">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-267">String</span></span>|  
|<span data-ttu-id="c6da7-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="c6da7-269">Byte</span><span class="sxs-lookup"><span data-stu-id="c6da7-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="c6da7-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="c6da7-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="c6da7-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c6da7-271">ColumnName</span></span>|<span data-ttu-id="c6da7-272">DataType</span><span class="sxs-lookup"><span data-stu-id="c6da7-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6da7-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="c6da7-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="c6da7-274">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-274">String</span></span>|  
|<span data-ttu-id="c6da7-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="c6da7-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="c6da7-276">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-276">String</span></span>|  
|<span data-ttu-id="c6da7-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="c6da7-278">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-278">String</span></span>|  
|<span data-ttu-id="c6da7-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-279">COLUMN_NAME</span></span>|<span data-ttu-id="c6da7-280">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-280">String</span></span>|  
|<span data-ttu-id="c6da7-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-281">COLUMN_TYPE</span></span>|<span data-ttu-id="c6da7-282">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-282">Int16</span></span>|  
|<span data-ttu-id="c6da7-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-283">DATA_TYPE</span></span>|<span data-ttu-id="c6da7-284">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-284">Int16</span></span>|  
|<span data-ttu-id="c6da7-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-285">TYPE_NAME</span></span>|<span data-ttu-id="c6da7-286">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-286">String</span></span>|  
|<span data-ttu-id="c6da7-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="c6da7-287">COLUMN_SIZE</span></span>|<span data-ttu-id="c6da7-288">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-288">Int32</span></span>|  
|<span data-ttu-id="c6da7-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c6da7-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="c6da7-290">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-290">Int32</span></span>|  
|<span data-ttu-id="c6da7-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="c6da7-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="c6da7-292">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-292">Int16</span></span>|  
|<span data-ttu-id="c6da7-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="c6da7-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="c6da7-294">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-294">Int16</span></span>|  
|<span data-ttu-id="c6da7-295">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="c6da7-295">NULLABLE</span></span>|<span data-ttu-id="c6da7-296">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-296">Int16</span></span>|  
|<span data-ttu-id="c6da7-297">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="c6da7-297">REMARKS</span></span>|<span data-ttu-id="c6da7-298">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-298">String</span></span>|  
|<span data-ttu-id="c6da7-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="c6da7-299">COLUMN_DEF</span></span>|<span data-ttu-id="c6da7-300">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-300">String</span></span>|  
|<span data-ttu-id="c6da7-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="c6da7-302">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-302">Int16</span></span>|  
|<span data-ttu-id="c6da7-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="c6da7-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="c6da7-304">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-304">Int16</span></span>|  
|<span data-ttu-id="c6da7-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c6da7-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="c6da7-306">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-306">Int32</span></span>|  
|<span data-ttu-id="c6da7-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c6da7-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="c6da7-308">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-308">Int32</span></span>|  
|<span data-ttu-id="c6da7-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="c6da7-309">IS_NULLABLE</span></span>|<span data-ttu-id="c6da7-310">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-310">String</span></span>|  
|<span data-ttu-id="c6da7-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="c6da7-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="c6da7-312">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-312">String</span></span>|  
|<span data-ttu-id="c6da7-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="c6da7-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="c6da7-314">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-314">String</span></span>|  
|<span data-ttu-id="c6da7-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="c6da7-316">Byte</span><span class="sxs-lookup"><span data-stu-id="c6da7-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="c6da7-317">Driver ODBC do Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="c6da7-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="c6da7-318">O Driver ODBC do Microsoft SQL Server Oracle suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="c6da7-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="c6da7-319">Tabelas</span><span class="sxs-lookup"><span data-stu-id="c6da7-319">Tables</span></span>  
  
-   <span data-ttu-id="c6da7-320">Colunas</span><span class="sxs-lookup"><span data-stu-id="c6da7-320">Columns</span></span>  
  
-   <span data-ttu-id="c6da7-321">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="c6da7-321">Procedures</span></span>  
  
-   <span data-ttu-id="c6da7-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="c6da7-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="c6da7-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="c6da7-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="c6da7-324">Exibições</span><span class="sxs-lookup"><span data-stu-id="c6da7-324">Views</span></span>  
  
-   <span data-ttu-id="c6da7-325">Índices</span><span class="sxs-lookup"><span data-stu-id="c6da7-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="c6da7-326">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="c6da7-326">Tables and Views</span></span>  
  
|<span data-ttu-id="c6da7-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c6da7-327">ColumnName</span></span>|<span data-ttu-id="c6da7-328">DataType</span><span class="sxs-lookup"><span data-stu-id="c6da7-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6da7-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c6da7-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="c6da7-330">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-330">String</span></span>|  
|<span data-ttu-id="c6da7-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6da7-331">TABLE_OWNER</span></span>|<span data-ttu-id="c6da7-332">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-332">String</span></span>|  
|<span data-ttu-id="c6da7-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-333">TABLE_NAME</span></span>|<span data-ttu-id="c6da7-334">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-334">String</span></span>|  
|<span data-ttu-id="c6da7-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-335">TABLE_TYPE</span></span>|<span data-ttu-id="c6da7-336">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-336">String</span></span>|  
|<span data-ttu-id="c6da7-337">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="c6da7-337">REMARKS</span></span>|<span data-ttu-id="c6da7-338">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="c6da7-339">Colunas</span><span class="sxs-lookup"><span data-stu-id="c6da7-339">Columns</span></span>  
  
|<span data-ttu-id="c6da7-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c6da7-340">ColumnName</span></span>|<span data-ttu-id="c6da7-341">DataType</span><span class="sxs-lookup"><span data-stu-id="c6da7-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6da7-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c6da7-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="c6da7-343">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-343">String</span></span>|  
|<span data-ttu-id="c6da7-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6da7-344">TABLE_OWNER</span></span>|<span data-ttu-id="c6da7-345">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-345">String</span></span>|  
|<span data-ttu-id="c6da7-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-346">TABLE_NAME</span></span>|<span data-ttu-id="c6da7-347">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-347">String</span></span>|  
|<span data-ttu-id="c6da7-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-348">COLUMN_NAME</span></span>|<span data-ttu-id="c6da7-349">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-349">String</span></span>|  
|<span data-ttu-id="c6da7-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-350">DATA_TYPE</span></span>|<span data-ttu-id="c6da7-351">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-351">Int16</span></span>|  
|<span data-ttu-id="c6da7-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-352">TYPE_NAME</span></span>|<span data-ttu-id="c6da7-353">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-353">String</span></span>|  
|<span data-ttu-id="c6da7-354">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="c6da7-354">PRECISION</span></span>|<span data-ttu-id="c6da7-355">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-355">Int32</span></span>|  
|<span data-ttu-id="c6da7-356">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="c6da7-356">LENGTH</span></span>|<span data-ttu-id="c6da7-357">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-357">Int32</span></span>|  
|<span data-ttu-id="c6da7-358">ESCALA</span><span class="sxs-lookup"><span data-stu-id="c6da7-358">SCALE</span></span>|<span data-ttu-id="c6da7-359">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-359">Int16</span></span>|  
|<span data-ttu-id="c6da7-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="c6da7-360">RADIX</span></span>|<span data-ttu-id="c6da7-361">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-361">Int16</span></span>|  
|<span data-ttu-id="c6da7-362">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="c6da7-362">NULLABLE</span></span>|<span data-ttu-id="c6da7-363">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-363">Int16</span></span>|  
|<span data-ttu-id="c6da7-364">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="c6da7-364">REMARKS</span></span>|<span data-ttu-id="c6da7-365">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-365">String</span></span>|  
|<span data-ttu-id="c6da7-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c6da7-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="c6da7-367">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="c6da7-368">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="c6da7-368">Procedures</span></span>  
  
|<span data-ttu-id="c6da7-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c6da7-369">ColumnName</span></span>|<span data-ttu-id="c6da7-370">DataType</span><span class="sxs-lookup"><span data-stu-id="c6da7-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6da7-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c6da7-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="c6da7-372">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-372">String</span></span>|  
|<span data-ttu-id="c6da7-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6da7-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="c6da7-374">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-374">String</span></span>|  
|<span data-ttu-id="c6da7-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="c6da7-376">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-376">String</span></span>|  
|<span data-ttu-id="c6da7-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="c6da7-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="c6da7-378">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-378">Int16</span></span>|  
|<span data-ttu-id="c6da7-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="c6da7-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="c6da7-380">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-380">Int16</span></span>|  
|<span data-ttu-id="c6da7-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="c6da7-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="c6da7-382">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-382">Int16</span></span>|  
|<span data-ttu-id="c6da7-383">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="c6da7-383">REMARKS</span></span>|<span data-ttu-id="c6da7-384">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-384">String</span></span>|  
|<span data-ttu-id="c6da7-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="c6da7-386">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="c6da7-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="c6da7-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="c6da7-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c6da7-388">ColumnName</span></span>|<span data-ttu-id="c6da7-389">DataType</span><span class="sxs-lookup"><span data-stu-id="c6da7-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6da7-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c6da7-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="c6da7-391">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-391">String</span></span>|  
|<span data-ttu-id="c6da7-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6da7-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="c6da7-393">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-393">String</span></span>|  
|<span data-ttu-id="c6da7-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="c6da7-395">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-395">String</span></span>|  
|<span data-ttu-id="c6da7-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-396">COLUMN_NAME</span></span>|<span data-ttu-id="c6da7-397">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-397">String</span></span>|  
|<span data-ttu-id="c6da7-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-398">COLUMN_TYPE</span></span>|<span data-ttu-id="c6da7-399">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-399">Int16</span></span>|  
|<span data-ttu-id="c6da7-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-400">DATA_TYPE</span></span>|<span data-ttu-id="c6da7-401">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-401">Int16</span></span>|  
|<span data-ttu-id="c6da7-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-402">TYPE_NAME</span></span>|<span data-ttu-id="c6da7-403">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-403">String</span></span>|  
|<span data-ttu-id="c6da7-404">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="c6da7-404">PRECISION</span></span>|<span data-ttu-id="c6da7-405">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-405">Int32</span></span>|  
|<span data-ttu-id="c6da7-406">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="c6da7-406">LENGTH</span></span>|<span data-ttu-id="c6da7-407">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-407">Int32</span></span>|  
|<span data-ttu-id="c6da7-408">ESCALA</span><span class="sxs-lookup"><span data-stu-id="c6da7-408">SCALE</span></span>|<span data-ttu-id="c6da7-409">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-409">Int16</span></span>|  
|<span data-ttu-id="c6da7-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="c6da7-410">RADIX</span></span>|<span data-ttu-id="c6da7-411">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-411">Int16</span></span>|  
|<span data-ttu-id="c6da7-412">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="c6da7-412">NULLABLE</span></span>|<span data-ttu-id="c6da7-413">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-413">Int16</span></span>|  
|<span data-ttu-id="c6da7-414">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="c6da7-414">REMARKS</span></span>|<span data-ttu-id="c6da7-415">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-415">String</span></span>|  
|<span data-ttu-id="c6da7-416">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="c6da7-416">OVERLOAD</span></span>|<span data-ttu-id="c6da7-417">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-417">Int32</span></span>|  
|<span data-ttu-id="c6da7-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c6da7-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="c6da7-419">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="c6da7-420">Microsoft Jet ODBC Driver</span><span class="sxs-lookup"><span data-stu-id="c6da7-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="c6da7-421">O Driver ODBC do Microsoft Jet suporta as seguintes coleções de esquema específico, além das coleções de esquema comuns:</span><span class="sxs-lookup"><span data-stu-id="c6da7-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="c6da7-422">Tabelas</span><span class="sxs-lookup"><span data-stu-id="c6da7-422">Tables</span></span>  
  
-   <span data-ttu-id="c6da7-423">Índices</span><span class="sxs-lookup"><span data-stu-id="c6da7-423">Indexes</span></span>  
  
-   <span data-ttu-id="c6da7-424">Colunas</span><span class="sxs-lookup"><span data-stu-id="c6da7-424">Columns</span></span>  
  
-   <span data-ttu-id="c6da7-425">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="c6da7-425">Procedures</span></span>  
  
-   <span data-ttu-id="c6da7-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="c6da7-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="c6da7-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="c6da7-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="c6da7-428">Exibições</span><span class="sxs-lookup"><span data-stu-id="c6da7-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="c6da7-429">Tabelas e exibições</span><span class="sxs-lookup"><span data-stu-id="c6da7-429">Tables and Views</span></span>  
  
|<span data-ttu-id="c6da7-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c6da7-430">ColumnName</span></span>|<span data-ttu-id="c6da7-431">DataType</span><span class="sxs-lookup"><span data-stu-id="c6da7-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6da7-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c6da7-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="c6da7-433">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-433">String</span></span>|  
|<span data-ttu-id="c6da7-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6da7-434">TABLE_OWNER</span></span>|<span data-ttu-id="c6da7-435">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-435">String</span></span>|  
|<span data-ttu-id="c6da7-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-436">TABLE_NAME</span></span>|<span data-ttu-id="c6da7-437">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-437">String</span></span>|  
|<span data-ttu-id="c6da7-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-438">TABLE_TYPE</span></span>|<span data-ttu-id="c6da7-439">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-439">String</span></span>|  
|<span data-ttu-id="c6da7-440">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="c6da7-440">REMARKS</span></span>|<span data-ttu-id="c6da7-441">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="c6da7-442">Colunas</span><span class="sxs-lookup"><span data-stu-id="c6da7-442">Columns</span></span>  
  
|<span data-ttu-id="c6da7-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c6da7-443">ColumnName</span></span>|<span data-ttu-id="c6da7-444">DataType</span><span class="sxs-lookup"><span data-stu-id="c6da7-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6da7-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c6da7-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="c6da7-446">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-446">String</span></span>|  
|<span data-ttu-id="c6da7-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6da7-447">TABLE_OWNER</span></span>|<span data-ttu-id="c6da7-448">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-448">String</span></span>|  
|<span data-ttu-id="c6da7-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-449">TABLE_NAME</span></span>|<span data-ttu-id="c6da7-450">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-450">String</span></span>|  
|<span data-ttu-id="c6da7-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-451">COLUMN_NAME</span></span>|<span data-ttu-id="c6da7-452">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-452">String</span></span>|  
|<span data-ttu-id="c6da7-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-453">DATA_TYPE</span></span>|<span data-ttu-id="c6da7-454">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-454">Int16</span></span>|  
|<span data-ttu-id="c6da7-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-455">TYPE_NAME</span></span>|<span data-ttu-id="c6da7-456">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-456">String</span></span>|  
|<span data-ttu-id="c6da7-457">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="c6da7-457">PRECISION</span></span>|<span data-ttu-id="c6da7-458">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-458">Int32</span></span>|  
|<span data-ttu-id="c6da7-459">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="c6da7-459">LENGTH</span></span>|<span data-ttu-id="c6da7-460">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-460">Int32</span></span>|  
|<span data-ttu-id="c6da7-461">ESCALA</span><span class="sxs-lookup"><span data-stu-id="c6da7-461">SCALE</span></span>|<span data-ttu-id="c6da7-462">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-462">Int16</span></span>|  
|<span data-ttu-id="c6da7-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="c6da7-463">RADIX</span></span>|<span data-ttu-id="c6da7-464">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-464">Int16</span></span>|  
|<span data-ttu-id="c6da7-465">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="c6da7-465">NULLABLE</span></span>|<span data-ttu-id="c6da7-466">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-466">Int16</span></span>|  
|<span data-ttu-id="c6da7-467">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="c6da7-467">REMARKS</span></span>|<span data-ttu-id="c6da7-468">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-468">String</span></span>|  
|<span data-ttu-id="c6da7-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c6da7-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="c6da7-470">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="c6da7-471">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="c6da7-471">Procedures</span></span>  
  
|<span data-ttu-id="c6da7-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c6da7-472">ColumnName</span></span>|<span data-ttu-id="c6da7-473">DataType</span><span class="sxs-lookup"><span data-stu-id="c6da7-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6da7-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c6da7-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="c6da7-475">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-475">String</span></span>|  
|<span data-ttu-id="c6da7-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6da7-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="c6da7-477">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-477">String</span></span>|  
|<span data-ttu-id="c6da7-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="c6da7-479">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-479">String</span></span>|  
|<span data-ttu-id="c6da7-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="c6da7-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="c6da7-481">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-481">Int16</span></span>|  
|<span data-ttu-id="c6da7-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="c6da7-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="c6da7-483">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-483">Int16</span></span>|  
|<span data-ttu-id="c6da7-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="c6da7-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="c6da7-485">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-485">Int16</span></span>|  
|<span data-ttu-id="c6da7-486">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="c6da7-486">REMARKS</span></span>|<span data-ttu-id="c6da7-487">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-487">String</span></span>|  
|<span data-ttu-id="c6da7-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="c6da7-489">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="c6da7-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="c6da7-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="c6da7-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c6da7-491">ColumnName</span></span>|<span data-ttu-id="c6da7-492">DataType</span><span class="sxs-lookup"><span data-stu-id="c6da7-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6da7-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="c6da7-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="c6da7-494">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-494">String</span></span>|  
|<span data-ttu-id="c6da7-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6da7-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="c6da7-496">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-496">String</span></span>|  
|<span data-ttu-id="c6da7-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="c6da7-498">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-498">String</span></span>|  
|<span data-ttu-id="c6da7-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-499">COLUMN_NAME</span></span>|<span data-ttu-id="c6da7-500">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-500">String</span></span>|  
|<span data-ttu-id="c6da7-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-501">COLUMN_TYPE</span></span>|<span data-ttu-id="c6da7-502">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-502">Int16</span></span>|  
|<span data-ttu-id="c6da7-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-503">DATA_TYPE</span></span>|<span data-ttu-id="c6da7-504">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-504">Int16</span></span>|  
|<span data-ttu-id="c6da7-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-505">TYPE_NAME</span></span>|<span data-ttu-id="c6da7-506">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-506">String</span></span>|  
|<span data-ttu-id="c6da7-507">PRECISÃO</span><span class="sxs-lookup"><span data-stu-id="c6da7-507">PRECISION</span></span>|<span data-ttu-id="c6da7-508">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-508">Int32</span></span>|  
|<span data-ttu-id="c6da7-509">COMPRIMENTO</span><span class="sxs-lookup"><span data-stu-id="c6da7-509">LENGTH</span></span>|<span data-ttu-id="c6da7-510">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-510">Int32</span></span>|  
|<span data-ttu-id="c6da7-511">ESCALA</span><span class="sxs-lookup"><span data-stu-id="c6da7-511">SCALE</span></span>|<span data-ttu-id="c6da7-512">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-512">Int16</span></span>|  
|<span data-ttu-id="c6da7-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="c6da7-513">RADIX</span></span>|<span data-ttu-id="c6da7-514">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-514">Int16</span></span>|  
|<span data-ttu-id="c6da7-515">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="c6da7-515">NULLABLE</span></span>|<span data-ttu-id="c6da7-516">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-516">Int16</span></span>|  
|<span data-ttu-id="c6da7-517">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="c6da7-517">REMARKS</span></span>|<span data-ttu-id="c6da7-518">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-518">String</span></span>|  
|<span data-ttu-id="c6da7-519">SOBRECARGA</span><span class="sxs-lookup"><span data-stu-id="c6da7-519">OVERLOAD</span></span>|<span data-ttu-id="c6da7-520">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-520">Int32</span></span>|  
|<span data-ttu-id="c6da7-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c6da7-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="c6da7-522">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="c6da7-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="c6da7-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="c6da7-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="c6da7-524">ColumnName</span></span>|<span data-ttu-id="c6da7-525">DataType</span><span class="sxs-lookup"><span data-stu-id="c6da7-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="c6da7-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="c6da7-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="c6da7-527">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-527">String</span></span>|  
|<span data-ttu-id="c6da7-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="c6da7-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="c6da7-529">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-529">String</span></span>|  
|<span data-ttu-id="c6da7-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="c6da7-531">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-531">String</span></span>|  
|<span data-ttu-id="c6da7-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-532">COLUMN_NAME</span></span>|<span data-ttu-id="c6da7-533">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-533">String</span></span>|  
|<span data-ttu-id="c6da7-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-534">COLUMN_TYPE</span></span>|<span data-ttu-id="c6da7-535">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-535">Int16</span></span>|  
|<span data-ttu-id="c6da7-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-536">DATA_TYPE</span></span>|<span data-ttu-id="c6da7-537">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-537">Int16</span></span>|  
|<span data-ttu-id="c6da7-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="c6da7-538">TYPE_NAME</span></span>|<span data-ttu-id="c6da7-539">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-539">String</span></span>|  
|<span data-ttu-id="c6da7-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="c6da7-540">COLUMN_SIZE</span></span>|<span data-ttu-id="c6da7-541">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-541">Int32</span></span>|  
|<span data-ttu-id="c6da7-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c6da7-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="c6da7-543">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-543">Int32</span></span>|  
|<span data-ttu-id="c6da7-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="c6da7-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="c6da7-545">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-545">Int16</span></span>|  
|<span data-ttu-id="c6da7-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="c6da7-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="c6da7-547">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-547">Int16</span></span>|  
|<span data-ttu-id="c6da7-548">PERMITE VALOR NULO</span><span class="sxs-lookup"><span data-stu-id="c6da7-548">NULLABLE</span></span>|<span data-ttu-id="c6da7-549">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-549">Int16</span></span>|  
|<span data-ttu-id="c6da7-550">COMENTÁRIOS</span><span class="sxs-lookup"><span data-stu-id="c6da7-550">REMARKS</span></span>|<span data-ttu-id="c6da7-551">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-551">String</span></span>|  
|<span data-ttu-id="c6da7-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="c6da7-552">COLUMN_DEF</span></span>|<span data-ttu-id="c6da7-553">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-553">String</span></span>|  
|<span data-ttu-id="c6da7-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="c6da7-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="c6da7-555">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-555">Int16</span></span>|  
|<span data-ttu-id="c6da7-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="c6da7-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="c6da7-557">Int16</span><span class="sxs-lookup"><span data-stu-id="c6da7-557">Int16</span></span>|  
|<span data-ttu-id="c6da7-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="c6da7-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="c6da7-559">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-559">Int32</span></span>|  
|<span data-ttu-id="c6da7-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="c6da7-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="c6da7-561">Int32</span><span class="sxs-lookup"><span data-stu-id="c6da7-561">Int32</span></span>|  
|<span data-ttu-id="c6da7-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="c6da7-562">IS_NULLABLE</span></span>|<span data-ttu-id="c6da7-563">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="c6da7-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6da7-564">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6da7-564">See Also</span></span>  
 <span data-ttu-id="c6da7-565">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c6da7-565">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
