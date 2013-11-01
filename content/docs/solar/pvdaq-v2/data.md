---
title: Raw Data (Deprecated)
summary: Obtain raw data from the PVDAQ system for a given date range.
url: GET /api/georeserv/app/pvdaq/data
disqus: true
deprecated: true

---

# {{title}} <span class="url">({{url}})</span>
{{summary}}

Note that you must [login](/doc/api/georeserv/login_handler/post) with your PVDAQ credentials to obtain an authorization cookie in order to utilize this service.

Also, if you are an admin or a PVDAQ admin, you can obtain data on behalf of another user by providing their user\_id as a parameter.

<ul id="toc"></ul>

## Request URL

<pre>GET http://developer.nrel.gov/api/georeserv/app/pvdaq/data<em>.format?parameters</em></pre>

## Request Parameters

<table border="0" cellpadding="0" cellspacing="0" class="doc-parameters">
  <thead>
    <tr>
      <th class="doc-parameters-name" scope="col">Parameter</th>
      <th class="doc-parameters-required" scope="col">Required</th>
      <th class="doc-parameters-value" scope="col">Value</th>
      <th class="doc-parameters-description" scope="col">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th class="doc-parameter-name" scope="row">format</th>
      <td class="doc-parameter-required">Yes</td>
      <td class="doc-parameter-value">
        <div class="doc-parameter-value-field">
          <strong>Type:</strong> string
        </div>
        <div class="doc-parameter-value-field">
          <strong>Default:</strong> None
        </div>
        <div class="doc-parameter-value-field">
          <strong>Options:</strong> <em>json</em>, <em>xml</em>, <em>csv</em>
        </div>
      </td>
      <td class="doc-parameter-description">
        <p>The output response format.</p>
      </td>
    </tr>
    <tr>
      <th class="doc-parameter-name" scope="row">api_key</th>
      <td class="doc-parameter-required">Yes</td>
      <td class="doc-parameter-value">
        <div class="doc-parameter-value-field">
          <strong>Type:</strong> string
        </div>
        <div class="doc-parameter-value-field">
          <strong>Default:</strong> None
        </div>
      </td>
      <td class="doc-parameter-description">
        <p>Your developer API key. See <a href="/doc/api-key">API keys</a> for more information.</p>
      </td>
    </tr>
    <tr>
      <th class="doc-parameter-name" scope="row">system_id</th>
      <td class="doc-parameter-required">Yes</td>
      <td class="doc-parameter-value">
        <div class="doc-parameter-value-field">
          <strong>Type:</strong> integer
        </div>
        <div class="doc-parameter-value-field">
          <strong>Default:</strong> None
        </div>
        <div class="doc-parameter-value-field"></div>
      </td>
      <td class="doc-parameter-description">
        <p>ID of the system you would like to query.</p>
      </td>
    </tr>
    <tr>
      <th class="doc-parameter-name" scope="row">start_date</th>
      <td class="doc-parameter-required">Yes</td>
      <td class="doc-parameter-value">
        <div class="doc-parameter-value-field">
          <strong>Type:</strong> date
        </div>
        <div class="doc-parameter-value-field">
          <strong>Default:</strong> None
        </div>
      </td>
      <td class="doc-parameter-description">
        <p>Start date of the query.</p>
      </td>
    </tr>
    <tr>
      <th class="doc-parameter-name" scope="row">end_date</th>
      <td class="doc-parameter-required">Yes</td>
      <td class="doc-parameter-value">
        <div class="doc-parameter-value-field">
          <strong>Type:</strong> date
        </div>
        <div class="doc-parameter-value-field">
          <strong>Default:</strong> None
        </div>
      </td>
      <td class="doc-parameter-description">
        <p>End date of the query. Note that the end date provided will include the last minute of that day</p>
      </td>
    </tr>
    <tr>
      <th class="doc-parameter-name" scope="row">user_id</th>
      <td class="doc-parameter-required">No</td>
      <td class="doc-parameter-value">
        <div class="doc-parameter-value-field">
          <strong>Type:</strong> string
        </div>
        <div class="doc-parameter-value-field">
          <strong>Default:</strong> None
        </div>
      </td>
      <td class="doc-parameter-description">
        <p>If you are an admin, ID of the user you would like to query on behalf of.</p>
      </td>
    </tr>
  </tbody>
</table>

## Response Fields

<table border="0" cellpadding="0" cellspacing="0" class="doc-parameters">
  <thead>
    <tr>
      <th class="doc-parameters-name" scope="col">Field</th>
      <th class="doc-parameters-value" scope="col">Value</th>
      <th class="doc-parameters-description" scope="col">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th class="doc-parameter-name" scope="row">errors</th>
      <td class="doc-parameter-value">
        <div class="doc-parameter-value-field">
          <strong>Type:</strong> list of dictionaries
        </div>
      </td>
      <td class="doc-parameter-description">
        <p>List of dictionaries containing errors that may be associated with an input field.</p>
      </td>
    </tr>
    <tr>
      <th class="doc-parameter-name" scope="row">infos</th>
      <td class="doc-parameter-value">
        <div class="doc-parameter-value-field">
          <strong>Type:</strong> list of dictionaries
        </div>
      </td>
      <td class="doc-parameter-description">
        <p>Non-error information about the inputs, or anything else in the system.</p>
      </td>
    </tr>
    <tr>
      <th class="doc-parameter-name" scope="row">inputs</th>
      <td class="doc-parameter-value">
        <div class="doc-parameter-value-field">
          <strong>Type:</strong> list of dictionaries
        </div>
      </td>
      <td class="doc-parameter-description">
        <p>List of the inputs as understood from the user.</p>
      </td>
    </tr>
    <tr>
      <th class="doc-parameter-name" scope="row">version</th>
      <td class="doc-parameter-value">
        <div class="doc-parameter-value-field">
          <strong>Type:</strong> string
        </div>
      </td>
      <td class="doc-parameter-description">
        <p>Version of Georeserv used to return this response.</p>
      </td>
    </tr>
    <tr>
      <th class="doc-parameter-name" scope="row">warnings</th>
      <td class="doc-parameter-value">
        <div class="doc-parameter-value-field">
          <strong>Type:</strong> list of dictionaries
        </div>
      </td>
      <td class="doc-parameter-description">
        <p>Warnings for the system, including information about coming deprecations to parameters, or to the call itself.</p>
      </td>
    </tr>
    <tr>
      <th class="doc-parameter-name" scope="row">outputs</th>
      <td class="doc-parameter-value">
        <div class="doc-parameter-value-field">
          <strong>Type:</strong> list of outputs
        </div>
      </td>
      <td class="doc-parameter-description">
        <p>First row in the list is the field names, remaining rows are the data, in this case in order by month.</p>
      </td>
    </tr>
  </tbody>
</table>

## Examples

### JSON Output Format

Note that if you have not logged in and obtained an authentication cookie for your session, this service will return a 404 error. Additionally, you will need to have access to the given system, in this case, the system with the system\_id of 13.

  -- --
     
  -- --

<pre>GET <a href="/api/georeserv/app/pvdaq/data.json?api_key=DEMO_KEY&amp;start_date=1/1/2011&amp;end_date=1/1/2011&amp;system_id=13">http://developer.nrel.gov/api/georeserv/app/pvdaq/data.json?api_key=DEMO_KEY&amp;start_date=1/1/2011&amp;end_date=1/1/2011&amp;system_id=13</a></pre>

```json
{'errors': [{}],
 'infos': [], 'inputs': {'end_date': '1/1/2011',
                         'start_date': '1/1/2011',
                         'system_id': '13'},
 'outputs': {'data': [[
                       'SiteID',                       
                       'Date-Time',
                       'ac_current',
                       'ac_power',
                       'ac_voltage',
                       'ambient_temp',
                       'das_temp',
                       'dc_pos_current',
                       'dc_pos_voltage',
                       'dc_power',
                       'inverter_temp',
                       'module_temp_1',
                       'module_temp_2',
                       'module_temp_3',
                       'poa_irradiance'],
                      [13,
                       '2011-01-01 00:00:00',
                       0.0011000000000000001,
                       0.5413,
                       122.6844,
                       -11.849,
                       -12.0228,
                       -0.0332,
                       9.1677999999999997,
                       -0.30380000000000001,
                       -12.9129,
                       -12.555400000000001,
                       -13.0547,
                       -12.9078,
                       -2.5508999999999999],
                      [13,
                       '2011-01-01 00:01:00',
                       0.00059999999999999995,
                       0.46229999999999999,
                       122.7055,
                       -11.919,
                       -12.0059,
                       -0.032800000000000003,
                       9.0718999999999994,
                       -0.2979,
                       -12.898899999999999,
                       -12.557499999999999,
                       -13.0708,
                       -12.914300000000001,
                       -2.4321999999999999],
                      [13,
                       '2011-01-01 00:02:00',
                       0.0011999999999999999,
                       0.53000000000000003,
                       122.7208,
                       -11.9573,
                       -12.0059,
                       -0.033700000000000001,
                       9.1480999999999995,
                       -0.30859999999999999,
                       -12.9055,
                       -12.5589,
                       -13.0517,
                       -12.8916,
                       -2.3134999999999999],
                      '...',
                      [13,
                       '2011-01-01 23:59:00',
                       0.0011999999999999999,
                       0.4284,
                       122.15949999999999,
                       -4.4880000000000004,
                       -6.7417999999999996,
                       -0.029000000000000001,
                       9.2436000000000007,
                       -0.2681,
                       -5.9264999999999999,
                       -6.4847999999999999,
                       -6.8434999999999997,
                       -6.7487000000000004,
                       -1.4232]],
             'groups': [],
             'headers': ['SiteID',
                         'Date-Time',
                         'ac_current',
                         'ac_power',
                         'ac_voltage',
                         'ambient_temp',
                         'das_temp',
                         'dc_pos_current',
                         'dc_pos_voltage',
                         'dc_power',
                         'inverter_temp',
                         'module_temp_1',
                         'module_temp_2',
                         'module_temp_3',
                         'poa_irradiance']},
 'version': '2.0.25',
 'warnings': []}
```

### XML Output Format

Note that if you have not logged in and obtained an authentication cookie for your session, this service will return a 404 error. Additionally, you will need to have access to the given system, in this case, the system with the system\_id of 13.

  -- --
     
  -- --

<pre>GET <a href="/api/georeserv/app/pvdaq/site_data.xml?system_id=13&amp;start_date=1/1/2011&amp;end_date=1/1/2011&amp;api_key=DEMO_KEY&amp;limit_fields=system_id&amp;limit_fields=measdatetime&amp;limit_fields=array_performance_ratio&amp;aggregate=weekly">http://developer.nrel.gov/api/georeserv/app/pvdaq/site_data.xml?system_id=13&amp;start_date=1/1/2011&amp;end_date=1/1/2011&amp;api_key=DEMO_KEY&amp;limit_fields=system_id&amp;limit_fields=measdatetime&amp;limit_fields=array_performance_ratio&amp;aggregate=weekly</a></pre>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<params>
  <param>
    <value>
      <array>
        <data/>
      </array>
    </value>
    <value>
      <string>
    errors
   </string>
    </value>
    <value>
      <array>
        <data/>
      </array>
    </value>
  </param>
  <param>
    <value>
      <array>
        <data/>
      </array>
    </value>
    <value>
      <string>
    infos
   </string>
    </value>
    <value>
      <array>
        <data/>
      </array>
    </value>
  </param>
  <param>
    <value>
      <array>
        <data/>
      </array>
    </value>
    <value>
      <string>
    inputs
   </string>
    </value>
    <value>
      <struct>
        <member>
          <name>
      aggregate
     </name>
        </member>
      </struct>
    </value>
    <value>
      <string>
    weekly
   </string>
    </value>
    <member>
      <name>
    system_id
   </name>
      <value>
        <string>
     13
    </string>
      </value>
    </member>
    <member>
      <name>
    start_date
   </name>
      <value>
        <string>
     1/1/2011
    </string>
      </value>
    </member>
    <member>
      <name>
    end_date
   </name>
      <value>
        <string>
     1/1/2011
    </string>
      </value>
    </member>
    <member>
      <name>
    limit_fields
   </name>
      <value>
        <array>
          <data/>
        </array>
      </value>
      <value>
        <string>
     system_id
    </string>
      </value>
      <value>
        <string>
     measdatetime
    </string>
      </value>
      <value>
        <string>
     array_performance_ratio
    </string>
      </value>
    </member>
  </param>
  <param>
    <value>
      <array>
        <data/>
      </array>
    </value>
    <value>
      <string>
    outputs
   </string>
    </value>
    <value>
      <array>
        <data/>
      </array>
    </value>
    <value>
      <array>
        <data/>
      </array>
    </value>
    <value>
      <string>
    measdatetime
   </string>
    </value>
    <value>
      <string>
    array_performance_ratio
   </string>
    </value>
    <value>
      <string>
    array_yield
   </string>
    </value>
    <value>
      <string>
    energy_from_grid
   </string>
    </value>
    <value>
      <string>
    reference_yield
   </string>
    </value>
    <value>
      <string>
    system_id
   </string>
    </value>
    <value>
      <array>
        <data/>
      </array>
    </value>
    <value>
      <string>
    2010-12-27 00:00:00
   </string>
    </value>
    <value>
      <double>
    0.63843111404086983
   </double>
    </value>
    <value>
      <double>
    19.138999999999992
   </double>
    </value>
    <value>
      <double>
    0.12300000000000007
   </double>
    </value>
    <value>
      <double>
    21.992999999999999
   </double>
    </value>
    <value>
      <int>
    13
   </int>
    </value>
  </param>
  <param>
    <value>
      <array>
        <data/>
      </array>
    </value>
    <value>
      <string>
    version
   </string>
    </value>
    <value>
      <string>
    2.0.25
   </string>
    </value>
  </param>
  <param>
    <value>
      <array>
        <data/>
      </array>
    </value>
    <value>
      <string>
    warnings
   </string>
    </value>
    <value>
      <array>
        <data/>
      </array>
    </value>
  </param>
</params>
```

## Rate Limits

[Standard rate limits](/docs/rate-limits) apply. No more than 1,000 requests may be made in any hour. No more than 10,000 requests may be made in any day.

## Errors

[Standard errors](/docs/errors) may be returned. In addition, the following service-specific errors may be returned:

<table border="0" cellpadding="0" cellspacing="0" class="doc-parameters">
  <thead>
    <tr>
      <th class="doc-parameters-name" scope="col">HTTP Status Code</th>
      <th class="doc-parameters-required" scope="col">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th class="doc-parameter-name" scope="row">400</th>
      <td class="doc-parameter-description">Invalid Request - One or more parameters did not pass validation, or a parameter may be missing. Check the <em>error</em> section of the response to see how the request url should be modified to address the error.</td>
    </tr>
  </tbody>
</table>