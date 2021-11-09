# Alaigal
Business application forum
package com.adm.Alaigal;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.Scanner;

public class Login {

	public static void main(String[] args) throws SQLException, ClassNotFoundException  {

		//Connecting JAVA to SQL using JDBC 
		
		Class.forName("org.postgresql.Driver");
		Connection connection = DriverManager.getConnection("jdbc:postgresql://localhost/Alaigal","postgres","Read@123");
		Statement stmnt = connection.createStatement();

		//To get the username and password input from console using Scanner
		
		Scanner name=new Scanner(System.in);
		System.out.println("Enter Username : ");
		String un=name.nextLine();

		Scanner password=new Scanner(System.in);
		System.out.println("Enter Password : ");
		String up=password.nextLine();

		//executing SQL query 
		String sql = "SELECT * FROM login WHERE username = '"+un+"' AND password ='"+up+"'";
		stmnt.execute(sql);
		ResultSet rs = stmnt.executeQuery(sql);

		//Check the Condition using If-else
		if(rs.next())
		{
			System.out.println("Login Successfully");

		}
		else{
			System.out.println("Incorrect credentials");
		}
		connection.close();
	}
}

