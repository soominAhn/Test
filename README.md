# Test
깃허브를 테스트해본당




















package com.spring.springboard;

import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;

public class JDBCUtil {
	public static Connection getConnection() {
		Connection conn = null;
		try {
			String driver = "oracle.jdbc.driver.OracleDriver";
			String url = "jdbc:oracle:thin:@localhost:1521:orcl";
			String oraId = "scott"; String oraPw = "123456";
			try {
				Class.forName(driver);
				conn = DriverManager.getConnection(url, oraId, oraPw);
			}
			catch (ClassNotFoundException e) {
				e.printStackTrace();
			}
			catch (SQLException e) {
				e.printStackTrace();
			}
		}
		catch (Exception e) {
			e.printStackTrace();
		}
		
		return conn;
	}
	
	public static void closeResource(Statement stmt, Connection conn) {
		try {
			if(stmt != null)
				stmt.close();
		}
		catch (Exception e) {
			stmt = null;
		}
		try {
			if(conn != null)
				conn.close();
		}
		catch (Exception e) {
			conn = null;
		}
	}
	
	public static void closeResource(ResultSet rs, Statement stmt, Connection conn) {
		try {
			if(rs != null)
				rs.close();
		}
		catch (Exception e) {
			rs = null;
		}
		try {
			if(stmt != null)
				stmt.close();
		}
		catch (Exception e) {
			stmt = null;
		}
		try {
			if(conn != null)
				conn.close();
		}
		catch (Exception e) {
			conn = null;
		}
	}

}
