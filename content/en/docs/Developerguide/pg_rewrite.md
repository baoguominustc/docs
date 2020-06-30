# PG\_REWRITE<a name="EN-US_TOPIC_0242385839"></a>

**PG\_REWRITE**  records rewrite rules defined for tables and views.

**Table  1**  PG\_REWRITE columns

<a name="en-us_topic_0237122311_en-us_topic_0059778039_t26ce538c6bb24f5183183c50c098e05f"></a>
<table><thead align="left"><tr id="en-us_topic_0237122311_en-us_topic_0059778039_re4f4128d4b854eff87d2f554361d4c82"><th class="cellrowborder" valign="top" width="21%" id="mcps1.2.4.1.1"><p id="en-us_topic_0237122311_en-us_topic_0059778039_afe06a4e2115046b9aacf7affe1d83de3"><a name="en-us_topic_0237122311_en-us_topic_0059778039_afe06a4e2115046b9aacf7affe1d83de3"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_afe06a4e2115046b9aacf7affe1d83de3"></a>Name</p>
</th>
<th class="cellrowborder" valign="top" width="21.5%" id="mcps1.2.4.1.2"><p id="en-us_topic_0237122311_en-us_topic_0059778039_a83eff0dae1174741ad18d2486cb8517c"><a name="en-us_topic_0237122311_en-us_topic_0059778039_a83eff0dae1174741ad18d2486cb8517c"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_a83eff0dae1174741ad18d2486cb8517c"></a>Type</p>
</th>
<th class="cellrowborder" valign="top" width="57.49999999999999%" id="mcps1.2.4.1.3"><p id="en-us_topic_0237122311_en-us_topic_0059778039_a92f709b0ce024c2dacb52f278e307770"><a name="en-us_topic_0237122311_en-us_topic_0059778039_a92f709b0ce024c2dacb52f278e307770"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_a92f709b0ce024c2dacb52f278e307770"></a>Description</p>
</th>
</tr>
</thead>
<tbody><tr id="en-us_topic_0237122311_row148317717541"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0237122311_p3831177185418"><a name="en-us_topic_0237122311_p3831177185418"></a><a name="en-us_topic_0237122311_p3831177185418"></a>oid</p>
</td>
<td class="cellrowborder" valign="top" width="21.5%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0237122311_p148327712547"><a name="en-us_topic_0237122311_p148327712547"></a><a name="en-us_topic_0237122311_p148327712547"></a>oid</p>
</td>
<td class="cellrowborder" valign="top" width="57.49999999999999%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0237122311_p4832117185410"><a name="en-us_topic_0237122311_p4832117185410"></a><a name="en-us_topic_0237122311_p4832117185410"></a>Row identifier (hidden attribute, which must be specified)</p>
</td>
</tr>
<tr id="en-us_topic_0237122311_en-us_topic_0059778039_r6b7cb14ec81a4d489e8dc09aff274304"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_a246ca060056d4417967455b04fbd3b5c"><a name="en-us_topic_0237122311_en-us_topic_0059778039_a246ca060056d4417967455b04fbd3b5c"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_a246ca060056d4417967455b04fbd3b5c"></a>rulename</p>
</td>
<td class="cellrowborder" valign="top" width="21.5%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_a01304f61813e4cc1a2a8f21733056dd2"><a name="en-us_topic_0237122311_en-us_topic_0059778039_a01304f61813e4cc1a2a8f21733056dd2"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_a01304f61813e4cc1a2a8f21733056dd2"></a>name</p>
</td>
<td class="cellrowborder" valign="top" width="57.49999999999999%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_a7ca40e83fb3042d3bdc95fa86aeed964"><a name="en-us_topic_0237122311_en-us_topic_0059778039_a7ca40e83fb3042d3bdc95fa86aeed964"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_a7ca40e83fb3042d3bdc95fa86aeed964"></a>Name of a rule</p>
</td>
</tr>
<tr id="en-us_topic_0237122311_en-us_topic_0059778039_r01cfd54656c54b74a7b4715e07d2734f"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_a7ad30c5c239b4f38b7e8d2ea86d96b01"><a name="en-us_topic_0237122311_en-us_topic_0059778039_a7ad30c5c239b4f38b7e8d2ea86d96b01"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_a7ad30c5c239b4f38b7e8d2ea86d96b01"></a>ev_class</p>
</td>
<td class="cellrowborder" valign="top" width="21.5%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_a4f47cf4a44c34353a88532f0f5c5d7a2"><a name="en-us_topic_0237122311_en-us_topic_0059778039_a4f47cf4a44c34353a88532f0f5c5d7a2"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_a4f47cf4a44c34353a88532f0f5c5d7a2"></a>oid</p>
</td>
<td class="cellrowborder" valign="top" width="57.49999999999999%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_a8774b7a2c1a747d9ac47b50f716ea600"><a name="en-us_topic_0237122311_en-us_topic_0059778039_a8774b7a2c1a747d9ac47b50f716ea600"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_a8774b7a2c1a747d9ac47b50f716ea600"></a>Name of the table that uses the rule</p>
</td>
</tr>
<tr id="en-us_topic_0237122311_en-us_topic_0059778039_rf4b46597e43a49259ddcc58086768287"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_a7897675549bb407d93668502e43e464f"><a name="en-us_topic_0237122311_en-us_topic_0059778039_a7897675549bb407d93668502e43e464f"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_a7897675549bb407d93668502e43e464f"></a>ev_attr</p>
</td>
<td class="cellrowborder" valign="top" width="21.5%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_acbc67741a9d74c20b8d8b8a5ec29d2ac"><a name="en-us_topic_0237122311_en-us_topic_0059778039_acbc67741a9d74c20b8d8b8a5ec29d2ac"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_acbc67741a9d74c20b8d8b8a5ec29d2ac"></a>smallint</p>
</td>
<td class="cellrowborder" valign="top" width="57.49999999999999%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_a6fa162ca7bd3450e856d6b1eba5cc49e"><a name="en-us_topic_0237122311_en-us_topic_0059778039_a6fa162ca7bd3450e856d6b1eba5cc49e"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_a6fa162ca7bd3450e856d6b1eba5cc49e"></a>Column to which this rule applies (always <strong id="en-us_topic_0237122311_b3361246161311"><a name="en-us_topic_0237122311_b3361246161311"></a><a name="en-us_topic_0237122311_b3361246161311"></a>0</strong> to indicate the entire table)</p>
</td>
</tr>
<tr id="en-us_topic_0237122311_en-us_topic_0059778039_rf53b565ecdd441fdb15cdeeb584405d3"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_adc7ec30bbd5e4c8890faaca107d15669"><a name="en-us_topic_0237122311_en-us_topic_0059778039_adc7ec30bbd5e4c8890faaca107d15669"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_adc7ec30bbd5e4c8890faaca107d15669"></a>ev_type</p>
</td>
<td class="cellrowborder" valign="top" width="21.5%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_a3661cad295d94ee8b2399ce834c34db7"><a name="en-us_topic_0237122311_en-us_topic_0059778039_a3661cad295d94ee8b2399ce834c34db7"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_a3661cad295d94ee8b2399ce834c34db7"></a>"char"</p>
</td>
<td class="cellrowborder" valign="top" width="57.49999999999999%" headers="mcps1.2.4.1.3 "><div class="p" id="en-us_topic_0237122311_en-us_topic_0059778039_ad5d80242c99e4e9bae38af228e6025ee"><a name="en-us_topic_0237122311_en-us_topic_0059778039_ad5d80242c99e4e9bae38af228e6025ee"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_ad5d80242c99e4e9bae38af228e6025ee"></a>Event type for this rule<a name="en-us_topic_0237122311_en-us_topic_0059778039_u2148ef1035724437ae72f596f2836eba"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_u2148ef1035724437ae72f596f2836eba"></a><ul id="en-us_topic_0237122311_en-us_topic_0059778039_u2148ef1035724437ae72f596f2836eba"><li>1 = SELECT</li><li>2 = UPDATE</li><li>3 = INSERT</li><li>4 = DELETE</li></ul>
</div>
</td>
</tr>
<tr id="en-us_topic_0237122311_en-us_topic_0059778039_rc25fbae47ee246b5875d9248dd4b09e5"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_a75bc8c254987423ab9afc74a5e8c08c8"><a name="en-us_topic_0237122311_en-us_topic_0059778039_a75bc8c254987423ab9afc74a5e8c08c8"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_a75bc8c254987423ab9afc74a5e8c08c8"></a>ev_enabled</p>
</td>
<td class="cellrowborder" valign="top" width="21.5%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_a54f09e4e9fea4d82846892afd8c10b79"><a name="en-us_topic_0237122311_en-us_topic_0059778039_a54f09e4e9fea4d82846892afd8c10b79"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_a54f09e4e9fea4d82846892afd8c10b79"></a>"char"</p>
</td>
<td class="cellrowborder" valign="top" width="57.49999999999999%" headers="mcps1.2.4.1.3 "><div class="p" id="en-us_topic_0237122311_en-us_topic_0059778039_a73fe04f618df4037ba3c689f2785ce0e"><a name="en-us_topic_0237122311_en-us_topic_0059778039_a73fe04f618df4037ba3c689f2785ce0e"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_a73fe04f618df4037ba3c689f2785ce0e"></a>Controls the mode in which the rule is triggered.<a name="en-us_topic_0237122311_en-us_topic_0059778039_ua2dce73ca63f46a78a9e83218970717d"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_ua2dce73ca63f46a78a9e83218970717d"></a><ul id="en-us_topic_0237122311_en-us_topic_0059778039_ua2dce73ca63f46a78a9e83218970717d"><li><strong id="en-us_topic_0237122311_b0487175820205"><a name="en-us_topic_0237122311_b0487175820205"></a><a name="en-us_topic_0237122311_b0487175820205"></a>O</strong>: The rule is triggered in origin and local modes.</li><li><strong id="en-us_topic_0237122311_b17696143632118"><a name="en-us_topic_0237122311_b17696143632118"></a><a name="en-us_topic_0237122311_b17696143632118"></a>D</strong>: The rule is disabled.</li><li><strong id="en-us_topic_0237122311_b129601446192112"><a name="en-us_topic_0237122311_b129601446192112"></a><a name="en-us_topic_0237122311_b129601446192112"></a>R</strong>: The rule is triggered in replica mode.</li><li><strong id="en-us_topic_0237122311_b1230511192224"><a name="en-us_topic_0237122311_b1230511192224"></a><a name="en-us_topic_0237122311_b1230511192224"></a>A</strong>: The rule is always triggered.</li></ul>
</div>
</td>
</tr>
<tr id="en-us_topic_0237122311_en-us_topic_0059778039_re9a2640991f145978899bcd19c5e2fe1"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_af410935095d9432493b69923f500d968"><a name="en-us_topic_0237122311_en-us_topic_0059778039_af410935095d9432493b69923f500d968"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_af410935095d9432493b69923f500d968"></a>is_instead</p>
</td>
<td class="cellrowborder" valign="top" width="21.5%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_a0c77fb840c1749c1ab96e4b1f478a93f"><a name="en-us_topic_0237122311_en-us_topic_0059778039_a0c77fb840c1749c1ab96e4b1f478a93f"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_a0c77fb840c1749c1ab96e4b1f478a93f"></a><span id="en-us_topic_0237122311_text1677261917281"><a name="en-us_topic_0237122311_text1677261917281"></a><a name="en-us_topic_0237122311_text1677261917281"></a>Boolean</span></p>
</td>
<td class="cellrowborder" valign="top" width="57.49999999999999%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_a73678c8c8f1044d984c48c0885673555"><a name="en-us_topic_0237122311_en-us_topic_0059778039_a73678c8c8f1044d984c48c0885673555"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_a73678c8c8f1044d984c48c0885673555"></a>The value is <strong id="en-us_topic_0237122311_b84235270621043"><a name="en-us_topic_0237122311_b84235270621043"></a><a name="en-us_topic_0237122311_b84235270621043"></a>true</strong> if the rule is of the <strong id="en-us_topic_0237122311_b76321320112218"><a name="en-us_topic_0237122311_b76321320112218"></a><a name="en-us_topic_0237122311_b76321320112218"></a>INSTEAD</strong> type.</p>
</td>
</tr>
<tr id="en-us_topic_0237122311_en-us_topic_0059778039_r8cca5d538dfb489ab1b5525af8192bc8"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_a523d10fca6a841939ce361bdf1f077d1"><a name="en-us_topic_0237122311_en-us_topic_0059778039_a523d10fca6a841939ce361bdf1f077d1"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_a523d10fca6a841939ce361bdf1f077d1"></a>ev_qual</p>
</td>
<td class="cellrowborder" valign="top" width="21.5%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_af5f100a549a64414a037926d418b83e2"><a name="en-us_topic_0237122311_en-us_topic_0059778039_af5f100a549a64414a037926d418b83e2"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_af5f100a549a64414a037926d418b83e2"></a>pg_node_tree</p>
</td>
<td class="cellrowborder" valign="top" width="57.49999999999999%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_a9884a20ffac34e4993004e3052fc3031"><a name="en-us_topic_0237122311_en-us_topic_0059778039_a9884a20ffac34e4993004e3052fc3031"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_a9884a20ffac34e4993004e3052fc3031"></a>Expression tree (in the form of a <strong id="en-us_topic_0237122311_b842352706114731"><a name="en-us_topic_0237122311_b842352706114731"></a><a name="en-us_topic_0237122311_b842352706114731"></a>nodeToString</strong>() representation) for the rule's qualifying condition</p>
</td>
</tr>
<tr id="en-us_topic_0237122311_en-us_topic_0059778039_r639dd3955c994ce6965a289ba7f2f465"><td class="cellrowborder" valign="top" width="21%" headers="mcps1.2.4.1.1 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_a47cd9d84210c4310af517f5fdfa3ee07"><a name="en-us_topic_0237122311_en-us_topic_0059778039_a47cd9d84210c4310af517f5fdfa3ee07"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_a47cd9d84210c4310af517f5fdfa3ee07"></a>ev_action</p>
</td>
<td class="cellrowborder" valign="top" width="21.5%" headers="mcps1.2.4.1.2 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_a54306980eff64fa8937dc50fa5d658fd"><a name="en-us_topic_0237122311_en-us_topic_0059778039_a54306980eff64fa8937dc50fa5d658fd"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_a54306980eff64fa8937dc50fa5d658fd"></a>pg_node_tree</p>
</td>
<td class="cellrowborder" valign="top" width="57.49999999999999%" headers="mcps1.2.4.1.3 "><p id="en-us_topic_0237122311_en-us_topic_0059778039_ab1ecab88b0aa4db3883b3448f7c33ce0"><a name="en-us_topic_0237122311_en-us_topic_0059778039_ab1ecab88b0aa4db3883b3448f7c33ce0"></a><a name="en-us_topic_0237122311_en-us_topic_0059778039_ab1ecab88b0aa4db3883b3448f7c33ce0"></a>Query tree (in the form of a <strong id="en-us_topic_0237122311_b842352706114740"><a name="en-us_topic_0237122311_b842352706114740"></a><a name="en-us_topic_0237122311_b842352706114740"></a>nodeToString</strong>() representation) for the rule's action</p>
</td>
</tr>
</tbody>
</table>
