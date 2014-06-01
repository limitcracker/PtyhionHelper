package com.johngift.vathmosapofoitisis;

import android.app.Activity;
import android.os.Bundle;
import android.view.View.OnClickListener;
import android.widget.ArrayAdapter;
import android.widget.EditText;
import android.widget.ListView;

public class MainActivity extends Activity {
	
	private EditText editTextCurrentMO;
	private EditText editTextPassedCourses;
	private EditText editTextTotalCourses;
	private EditText editTextWantedMO;
	private ListView listViewResults;
	private android.widget.Button calculateButton;
	
	@Override
	protected void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);
		setContentView(R.layout.activity_main);
		
		editTextCurrentMO = (EditText)findViewById(R.id.currentmo_edittext);
		editTextPassedCourses = (EditText)findViewById(R.id.passed_edittext);
		editTextTotalCourses = (EditText)findViewById(R.id.total_edittext);
		editTextWantedMO = (EditText)findViewById(R.id.wanted_edittext);
		listViewResults = (ListView)findViewById(R.id.result_list);
		
		calculateButton = (android.widget.Button)findViewById(R.id.calculate_button);
		calculateButton.setOnClickListener(new OnClickListener() {
			public void onClick(android.view.View v) {
				calculateMO();
			}
		});
		
	}
	
	private void calculateMO(){
		double currentMO = Double.parseDouble(editTextCurrentMO.getText().toString());
		double passedCourses = Double.parseDouble(editTextPassedCourses.getText().toString());
		double totalCourses = Double.parseDouble(editTextTotalCourses.getText().toString());
		double wantedMO = Double.parseDouble(editTextWantedMO.getText().toString());
		
		double examinedMO;
		
		String[] values = getResources().getStringArray(R.array.results_list);
		ArrayAdapter<String> adapter = new ArrayAdapter<String>(this, android.R.layout.simple_list_item_1, values);
		listViewResults.setAdapter(adapter);
		
		
		String strNotEnough = "";
		String strEnough = "";
		
		int c = 0;
		for(int i=(int)Math.floor(wantedMO); i < 11; i++){
			examinedMO = ((currentMO * passedCourses) + (i*(totalCourses - passedCourses)))/totalCourses;
			
			if(examinedMO < wantedMO){
				strNotEnough = "If you get "+ (totalCourses - passedCourses) + "-> " + i + "s it's not enough\n";
				values[c++] = strNotEnough;
			}else{
				strEnough = "If you get "+ (totalCourses - passedCourses) + "-> " + i + "s you 'll graduate with " + examinedMO + "\n";
				values[c++] = strEnough;
			}
		}
		
	}

}
