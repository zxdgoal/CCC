package uk.ac.ncl.amazon;

import java.io.File;
import java.io.InputStream;

import com.amazonaws.auth.ClasspathPropertiesFileCredentialsProvider;
import com.amazonaws.regions.Region;
import com.amazonaws.regions.Regions;
import com.amazonaws.services.s3.AmazonS3;
import com.amazonaws.services.s3.AmazonS3Client;
import com.amazonaws.services.s3.model.GetObjectRequest;
import com.amazonaws.services.s3.model.ObjectMetadata;
import com.amazonaws.services.s3.model.PutObjectRequest;
import com.amazonaws.services.s3.model.S3Object;

public class S3
{
	private AmazonS3 s3;
	private final String bucketName = "rdrepository";

	public S3()
	{
		s3 = new AmazonS3Client(new ClasspathPropertiesFileCredentialsProvider());
		Region usWest2 = Region.getRegion(Regions.US_WEST_2);
		s3.setRegion(usWest2);
	}

	public void upload(File file, String key)
	{
		s3.putObject(new PutObjectRequest(bucketName, key, file));
	}
	
	public void upload(InputStream is, String key, ObjectMetadata metadata)
	{
		s3.putObject(bucketName, key, is, metadata);
	}
	
	public S3Object download(String key)
	{
		return s3.getObject(new GetObjectRequest(bucketName, key));
	}
	
	public void delete(String key)
	{
		 s3.deleteObject(bucketName, key);
	}
	
}
