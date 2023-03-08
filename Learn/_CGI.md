# Things to study for CGI/USCIS

org.springframework. 

@Profile({"default"}) .context.
@Configuration .context.
@ConfigurationProperties("spring.datasource.oracle.dev") .boot.context.
@EnableScheduling .scheduling.
@Bean .context.

@NotNull javax.validation.constraints.NotNull

JSONObject resp = new JSONObject(String);
resp.put("code", code);
JSONObject body = resp.optJSONObject("body");
int responseCode = body.optInt("returnCode", 7);

JSONArray array = new JSONArray();
JSONArray array = body.optJSONArray("details");

for(int i; i< array.length(); i++){
    JSONObject current = array.getJSONObject(i);
}
